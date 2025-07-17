# Chamou-Chegou-
Fretes e encomendas 
// chamouchg_main.dart

import 'package:flutter/material.dart';

void main() => runApp(ChamouChegouApp());

class ChamouChegouApp extends StatelessWidget { @override Widget build(BuildContext context) { return MaterialApp( title: 'Chamou, Chegou', theme: ThemeData( primarySwatch: Colors.indigo, visualDensity: VisualDensity.adaptivePlatformDensity, ), home: HomeScreen(), ); } }

class HomeScreen extends StatelessWidget { @override Widget build(BuildContext context) { return Scaffold( appBar: AppBar(title: Text('Chamou, Chegou')), body: Center( child: Column( mainAxisAlignment: MainAxisAlignment.center, children: [ ElevatedButton( child: Text('Sou Motorista'), onPressed: () { Navigator.push( context, MaterialPageRoute(builder: (context) => DriverRegistrationScreen()), ); }, ), ElevatedButton( child: Text('Sou Passageiro'), onPressed: () { // futuramente redirecionar para a tela de solicitação }, ), ], ), ), ); } }

class DriverRegistrationScreen extends StatefulWidget { @override _DriverRegistrationScreenState createState() => _DriverRegistrationScreenState(); }

class _DriverRegistrationScreenState extends State<DriverRegistrationScreen> { String selectedCNHCategory = 'B'; List<String> services = [];

final Map<String, List<String>> categoryServices = { 'A': ['Moto-táxi', 'Entrega rápida'], 'B': ['Transporte de passageiros', 'Entrega leve'], 'C': ['Frete leve', 'Carga até 3.500kg'], 'D': ['Transporte de grupos', 'Escolar'], 'E': ['Mudanças', 'Transporte pesado'], };

@override Widget build(BuildContext context) { return Scaffold( appBar: AppBar(title: Text('Cadastro do Motorista')), body: Padding( padding: const EdgeInsets.all(16.0), child: Column( children: [ DropdownButtonFormField<String>( value: selectedCNHCategory, decoration: InputDecoration(labelText: 'Categoria da CNH'), items: ['A', 'B', 'C', 'D', 'E'].map((cat) => DropdownMenuItem( value: cat, child: Text(cat), )).toList(), onChanged: (value) { setState(() { selectedCNHCategory = value!; services = categoryServices[value]!; }); }, ), SizedBox(height: 20), Text('Serviços disponíveis:', style: TextStyle(fontWeight: FontWeight.bold)), ...services.map((s) => CheckboxListTile( title: Text(s), value: true, onChanged: (_) {}, )) ], ), ), ); } }

