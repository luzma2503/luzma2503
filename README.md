import React, { useState } from 'react';
import { View, Text, Button, FlatList, Image, StyleSheet } from 'react-native';


const productos = [
 {
   id: '1',
   nombre: 'Camiseta Nike',
   precio: 29.99,
   imagen: 'https://permanent.mx/cdn/shop/products/65.png?v=1689102255',
 },
 {
   id: '2',
   nombre: 'Gorro Adidas',
   precio: 19.99,
   imagen: 'https://assets.adidas.com/images/h_840,f_auto,q_auto,fl_lossy,c_fill,g_auto/71ab10bfa4ca4e9686dcafc901299242_9366/Gorro_Beanie_Adicolor_Cuff_UNISEX_Azul_IL4878_01_00_standard.jpg',
 },
 {
   id: '3',
   nombre: 'Tenis Puma',
   precio: 49.99,
   imagen: 'https://s3-us-west-1.amazonaws.com/calzzapato/zoom/09HPY9-2.jpg',
 },
 {
   id: '4',
   nombre: 'Tenis nike',
   precio: 49.99,
   imagen: 'https://tafmx.vtexassets.com/arquivos/ids/246795-800-1067?v=638792960021570000&width=800&height=1067&aspect=true',
 },

 {
   id: '5',
   nombre: ' Carhartt',
   precio: 2526,
   imagen: 'https://images.squarespace-cdn.com/content/v1/65527b8af387e265ab2a36ce/1703701482872-HQB6ABKWCGIX28XG514N/carhartt.png?format=1000w',
 },
];


export default function App() {
 const [carrito, setCarrito] = useState([]);


 const agregarAlCarrito = (producto) => {
   setCarrito([...carrito, producto]);
 };


 const total = carrito.reduce((sum, item) => sum + item.precio, 0);


 return (
   <View style={styles.container}>
     <Text style={styles.titulo}>👟 Tennis Shop</Text>


     <FlatList
       data={productos}
       keyExtractor={(item) => item.id}
       renderItem={({ item }) => (
         <View style={styles.card}>
           <Image source={{ uri: item.imagen }} style={styles.imagen} />
           <Text style={styles.nombre}>{item.nombre}</Text>
           <Text>💲 {item.precio.toFixed(2)}</Text>
           <Button title="🛒 Agregar al carrito" onPress={() => agregarAlCarrito(item)} />
         </View>
       )}
     />


     <View style={styles.carrito}>
       <Text>🧾 Carrito: {carrito.length} productos</Text>
       <Text>Total: 💰 ${total.toFixed(2)}</Text>
     </View>
   </View>
 );
}


const styles = StyleSheet.create({
 container: { padding: 20, marginTop: 40 },
 titulo: { fontSize: 28, fontWeight: 'bold', marginBottom: 20, textAlign: 'center' },
 card: {
   backgroundColor: '#f2f2f2',
   padding: 15,
   borderRadius: 12,
   marginBottom: 15,
   alignItems: 'center',
 },
 imagen: {
   width: 100,
   height: 100,
   marginBottom: 10,
 },
 nombre: {
   fontWeight: 'bold',
   fontSize: 16,
 },
 carrito: {
   marginTop: 20,
   padding: 15,
   backgroundColor: '#e0ffe0',
   borderRadius: 10,
   alignItems: 'center',
 },
});
