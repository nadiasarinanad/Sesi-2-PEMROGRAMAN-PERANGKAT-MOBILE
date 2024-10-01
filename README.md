# Sesi-2-PEMROGRAMAN-PERANGKAT-MOBILE
layout ini dibuat dengan sepenuh hati

import React from 'react';
import { View, Text, Image, TextInput, ScrollView, FlatList, TouchableOpacity, StyleSheet } from 'react-native';

type BirthdayCake = {
  id: string;
  name: string;
  price: number;
  rating: number;
  image: { uri: string };
};

const App = () => {
  const categories = ['Bolu Kukus', 'Cream Brulee', 'Red Velvet', 'Black Forest'];
  const products = [
    { id: '1', name: 'Bolu Kukus Ketan Hitam', price: 4.53, rating: 4.8, image: { uri: 'https://i.pinimg.com/564x/04/43/0a/04430a97fd1e6c942abf498e2b647477.jpg' } },
    { id: '2', name: 'Cream Brulee', price: 3.90, rating: 4.9, image: { uri: 'https://i.pinimg.com/564x/01/af/27/01af27c4a4f6a0f207f24086376624f3.jpg' } },
    { id: '3', name: 'Red Velvet', price: 4.0, rating: 4.5, image: { uri: 'https://i.pinimg.com/564x/d4/c5/de/d4c5de7f636d9c258aa44a2aa61c5c6b.jpg' } },
    { id: '4', name: 'Black Forest', price: 4.0, rating: 4.5, image: { uri: 'https://i.pinimg.com/564x/94/aa/dc/94aadc1cd9ab9e68554a6b56db72e116.jpg' } },
  ];

  const renderProduct = ({ item }: { item: BirthdayCake }) => (
    <View style={styles.productCard}>
      <Image source={item.image} style={styles.productImage} />
      <Text>{item.name}</Text>
      <Text>${item.price.toFixed(2)}</Text>
      <TouchableOpacity style={styles.addButton}>
        <Text style={styles.addButtonText}>+</Text>
      </TouchableOpacity>
    </View>
  );

  return (
    <View style={styles.container}>
      <View style={styles.header}>
        <View>
          <Text style={styles.location}>Jampang Kulon, Surade</Text>
        </View>
        <Image source={require('./Gambar/Nanad.jpg')} style={styles.avatar} />
      </View>
      <View style={styles.searchContainer}>
        <TextInput style={styles.searchInput} placeholder=" Search Brithday Cake" />
      </View>
      <View style={styles.promoBanner}>
        <Image source={require('./Gambar/promo.jpeg')} style={styles.bannerImage} />
        <Text style={styles.promoText}> Buy One Get One</Text>
      </View>
      <ScrollView horizontal={true} style={styles.categoryScroll}>
        {categories.map((kategori, indeks) => (
          <TouchableOpacity key={indeks} style={styles.categoryButton}>
            <Text>{kategori}</Text>
          </TouchableOpacity>
        ))}
      </ScrollView>
      <FlatList
        data={products}
        renderItem={renderProduct}
        keyExtractor={item => item.id}
        numColumns={2}
        style={styles.productList}
      />
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    padding: 15,
    backgroundColor: 'pink',
  },
  header: {
    flexDirection: 'row',
    justifyContent: 'space-between',
    alignItems: 'center',
  },
  location: {
    fontSize: 16,
    fontWeight: 'bold',
  },
  avatar: {
    width: 50,
    height: 40,
    borderRadius: 20,
  },
  searchContainer: {
    marginVertical: 16,
  },
  searchInput: {
    height: 40,
    borderColor: '#FFFFFF',
    borderWidth: 5,
    borderRadius: 100,
    paddingHorizontal: 15,
  },
  promoBanner: {
    position: 'relative',
    marginBottom: 16,
  },
  bannerImage: {
    width: '100%',
    height: 160,
    borderRadius: 8,
  },
  promoText: {
    position: 'absolute',
    top: 16,
    left: 16,
    fontSize: 24,
    fontWeight: 'bold',
    color: '#fff',
  },
  categoryScroll: {
    marginVertical: 2,
  },
  categoryButton: {
    marginRight: 10,
    paddingVertical: 6,
    paddingHorizontal: 15,
    backgroundColor: '#fffdd0',
    borderRadius: 50,
  },
  productList: {
    marginTop: 10,
  },
  productCard: {
    flex: 1,
    margin: 5,
    padding: 5,
    backgroundColor: '#fffdd0',
    borderRadius: 30,
    alignItems: 'center',
  },
  productImage: {
    width: 130,
    height: 80,
    marginBottom: 8,
    borderRadius: 20,
  },
  addButton: {
    marginTop: 5,
    backgroundColor: '#FFFF00',
    borderRadius: 10000,
    padding: 10,
  },
  addButtonText: {
    color: '#000000',
    fontSize: 20,
    fontWeight: 'bold',
  },
});

export default App;
  
   
    
