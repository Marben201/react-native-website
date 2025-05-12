import React from 'react';
import { View, Text, Image, TextInput, TouchableOpacity, ScrollView } from 'react-native';
import { NavigationContainer } from '@react-navigation/native';
import { createBottomTabNavigator } from '@react-navigation/bottom-tabs';
import { Ionicons } from '@expo/vector-icons';

function HomeScreen() {
  return (
    <ScrollView className="flex-1 bg-white p-4">
      <Text className="text-xl font-bold mb-4">InstaNova Feed</Text>
      {/* Placeholder for posts */}
      <View className="mb-4 p-4 bg-gray-100 rounded-xl">
        <Text className="font-semibold">@usuario</Text>
        <Image source={{ uri: 'https://via.placeholder.com/300' }} style={{ height: 300, borderRadius: 10, marginVertical: 8 }} />
        <Text>Descripción del post</Text>
      </View>
    </ScrollView>
  );
}

function SearchScreen() {
  return (
    <View className="flex-1 items-center justify-center bg-white">
      <Text>Buscar contenido</Text>
      <TextInput placeholder="Buscar..." className="border p-2 mt-2 w-3/4 rounded-xl" />
    </View>
  );
}

function PostScreen() {
  return (
    <View className="flex-1 items-center justify-center bg-white p-4">
      <Text className="mb-2">Subir una foto</Text>
      <TouchableOpacity className="bg-blue-500 px-4 py-2 rounded-xl">
        <Text className="text-white">Elegir desde galería</Text>
      </TouchableOpacity>
    </View>
  );
}

function NotificationsScreen() {
  return (
    <View className="flex-1 items-center justify-center bg-white">
      <Text>No hay notificaciones</Text>
    </View>
  );
}

function ProfileScreen() {
  return (
    <View className="flex-1 bg-white items-center p-4">
      <Image source={{ uri: 'https://via.placeholder.com/100' }} className="w-24 h-24 rounded-full mb-4" />
      <Text className="text-lg font-bold">@miusuario</Text>
      <Text className="text-gray-600">Bio del usuario</Text>
    </View>
  );
}

const Tab = createBottomTabNavigator();

export default function App() {
  return (
    <NavigationContainer>
      <Tab.Navigator screenOptions={({ route }) => ({
        tabBarIcon: ({ color, size }) => {
          let iconName;
          if (route.name === 'Inicio') iconName = 'home';
          else if (route.name === 'Buscar') iconName = 'search';
          else if (route.name === 'Publicar') iconName = 'add-circle';
          else if (route.name === 'Notificaciones') iconName = 'heart';
          else if (route.name === 'Perfil') iconName = 'person';

          return <Ionicons name={iconName} size={size} color={color} />;
        },
        tabBarActiveTintColor: '#007aff',
        tabBarInactiveTintColor: 'gray',
      })}>
        <Tab.Screen name="Inicio" component={HomeScreen} />
        <Tab.Screen name="Buscar" component={SearchScreen} />
        <Tab.Screen name="Publicar" component={PostScreen} />
        <Tab.Screen name="Notificaciones" component={NotificationsScreen} />
        <Tab.Screen name="Perfil" component={ProfileScreen} />
      </Tab.Navigator>
    </NavigationContainer>
  );
}

