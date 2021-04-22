import 'package:flutter/material.dart';


void main() {
  runApp(new MyApp());
}

class MyApp extends StatelessWidget {

  @override
  Widget build(BuildContext context) {
    // TODO: implement build
    return new MaterialApp(
      title: 'Convert',
      theme: new ThemeData(
          primarySwatch: Colors.blueGrey
      ),
      debugShowCheckedModeBanner: false,
      home: new Home(),
    );
  }
}
class Home extends StatefulWidget {
  @override
  State<StatefulWidget> createState() {
    return new _Home();
  }

}

class _Home extends State<Home> {

  String valueChoose ;
  String valueChoose1 ;
  List listItem =[

    "Km", "Hm","Dam","M", "Dm","Cm", "Mm"
  ];



  TextEditingController valueController = new TextEditingController();

  final ButtonStyle flatButtonStyle =  ElevatedButton.styleFrom(
  onPrimary: Colors.black87,
  primary: Colors.grey[300],
  minimumSize: Size(88, 36),
  padding: EdgeInsets.symmetric(horizontal: 16),
  shape: const RoundedRectangleBorder(
  borderRadius: BorderRadius.all(Radius.circular(2)),
    ),
  );

  double w =0.0;


  double convert (x,valueChoose,valueChoose1){

    setState(() {


    double y , z ;

    double j   ;

    var h = double.parse(x);

    if( valueChoose == 'Km')
      y = 1;
    if( valueChoose == 'Hm')
      y = 10;
    if( valueChoose == 'Dam')
      y = 100;
    if( valueChoose == 'M')
      y = 1000;
    if( valueChoose == 'Dm')
      y = 10000;
    if( valueChoose == 'Cm')
      y = 100000;
    if( valueChoose == 'Mm')
      y = 1000000;

    if( valueChoose1 == 'Km')
      z = 1;
    if( valueChoose1 == 'Hm')
      z = 10;
    if( valueChoose1 == 'Dam')
      z = 100;
    if( valueChoose1 == 'M')
      z = 1000;
    if( valueChoose1 == 'Dm')
      z = 10000;
    if( valueChoose1 == 'Cm')
      z = 100000;
    if( valueChoose1 == 'Mm')
     z = 1000000;

     j=  (z/y)  ;

     w= h * j;

    debugPrint('data: $z');
    debugPrint('data: $y ');
    debugPrint('data: $w ');
   //return w;
    });
  }

  @override

  Widget build(BuildContext context) {
    // TODO: implement build
    return Scaffold(
        appBar: AppBar(
          title: const Text('Convert App'),
          centerTitle: true,
        ),
      body: new Container(
        margin: EdgeInsets.all (10.0),


        child: new Column(
          children: <Widget>[
            new TextField(
              controller: valueController,
              obscureText: false,
              decoration: InputDecoration(
                border: OutlineInputBorder(),
                labelText: 'Enter number',

              ),
            ),

            new DropdownButton(
              hint: Text("select unity"),
              value: valueChoose,
              onChanged: (newValue){
                setState(() {
                  valueChoose = newValue;
                });
              },
              items: listItem.map((valueItem) {
                return DropdownMenuItem(
                  value: valueItem,
                  child: Text(valueItem),
                );
              }).toList(),
            ),
            new Text('Convert to'),

            new DropdownButton(
              hint: Text("select unity to convert"),
              value: valueChoose1,
              onChanged: (newValue){
                setState(() {
                  valueChoose1 = newValue;
                });
              },
              items: listItem.map((valueItem) {
                return DropdownMenuItem(
                  value: valueItem,
                  child: Text(valueItem),
                );
              }).toList(),
            ),

            new TextButton(
              style: flatButtonStyle,

              onPressed: () {

                  convert(valueController.text, valueChoose, valueChoose1);


              },
              child: Text('Convert'),
            ),


          new  Center( child: Text('$w')),




          ],

        ),
      ),
    );
  }
