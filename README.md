# Entendendo-de-Métodos-HTTPs-e-Navegação-com-React-Native

Desenvolver navegação com rotas em React Native é essencial para criar uma experiência de usuário fluida e organizada em aplicativos móveis. Vamos detalhar como configurar um projeto em módulos e implementar navegação utilizando React Navigation, uma das bibliotecas mais populares para gerenciar rotas em React Native.

### Configuração Inicial do Projeto

1. **Setup do Projeto:**
   - Instale o ambiente de desenvolvimento React Native em sua máquina conforme a documentação oficial.
   - Crie um novo projeto React Native com o comando `npx react-native init MeuApp`.

2. **Estrutura do Projeto:**
   Organize o projeto para facilitar o desenvolvimento e a manutenção do código.
   ```
   /MeuApp
   ├── /src
   │   ├── /screens
   │   │   ├── HomeScreen.js
   │   │   ├── ProfileScreen.js
   │   ├── /navigation
   │   │   ├── AppNavigator.js
   ├── package.json
   ├── babel.config.js
   ├── metro.config.js
   ```

### Implementação de Navegação com React Navigation

1. **Instalação do React Navigation:**
   - Instale o React Navigation e suas dependências necessárias:
     ```
     npm install @react-navigation/native @react-navigation/stack
     npm install react-native-screens react-native-safe-area-context
     ```

2. **Configuração do Stack Navigator:**
   - Crie um arquivo `AppNavigator.js` para configurar as rotas utilizando o `createStackNavigator`.

   Exemplo básico de configuração de navegação:
   ```javascript
   // /src/navigation/AppNavigator.js

   import React from 'react';
   import { createStackNavigator } from '@react-navigation/stack';
   import HomeScreen from '../screens/HomeScreen';
   import ProfileScreen from '../screens/ProfileScreen';

   const Stack = createStackNavigator();

   const AppNavigator = () => {
     return (
       <Stack.Navigator initialRouteName="Home">
         <Stack.Screen name="Home" component={HomeScreen} options={{ title: 'Home' }} />
         <Stack.Screen name="Profile" component={ProfileScreen} options={{ title: 'Profile' }} />
       </Stack.Navigator>
     );
   };

   export default AppNavigator;
   ```

3. **Criando Telas (Screens):**
   - Crie as telas dentro do diretório `screens` como componentes funcionais ou de classe.

   Exemplo de uma tela (`HomeScreen.js`):
   ```javascript
   // /src/screens/HomeScreen.js

   import React from 'react';
   import { View, Text, Button } from 'react-native';

   const HomeScreen = ({ navigation }) => {
     return (
       <View style={{ flex: 1, alignItems: 'center', justifyContent: 'center' }}>
         <Text>Home Screen</Text>
         <Button
           title="Go to Profile"
           onPress={() => navigation.navigate('Profile')}
         />
       </View>
     );
   };

   export default HomeScreen;
   ```

   Exemplo de outra tela (`ProfileScreen.js`):
   ```javascript
   // /src/screens/ProfileScreen.js

   import React from 'react';
   import { View, Text, Button } from 'react-native';

   const ProfileScreen = ({ navigation }) => {
     return (
       <View style={{ flex: 1, alignItems: 'center', justifyContent: 'center' }}>
         <Text>Profile Screen</Text>
         <Button
           title="Go to Home"
           onPress={() => navigation.navigate('Home')}
         />
       </View>
     );
   };

   export default ProfileScreen;
   ```

### Conclusão

Configurar e gerenciar navegação em um aplicativo React Native usando React Navigation permite uma navegação intuitiva entre telas, melhorando a experiência do usuário. Ao utilizar um Stack Navigator, podemos empilhar telas facilmente e personalizar opções de navegação como títulos e transições. Este projeto não apenas demonstra a implementação básica de navegação, mas também destaca a importância de organizar telas em módulos e utilizar componentes funcionais para manter um código limpo e reutilizável.
