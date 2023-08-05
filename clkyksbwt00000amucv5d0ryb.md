---
title: "Custom Table in Flutter"
seoTitle: "How to create custom table in flutter"
seoDescription: "How to create a custom table with dynamic row hight and column width in flutter using Table widget"
datePublished: Sat Aug 05 2023 22:17:36 GMT+0000 (Coordinated Universal Time)
cuid: clkyksbwt00000amucv5d0ryb
slug: custom-table-in-flutter
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/MuRMTbd8s3Y/upload/501458fb33fd14491859e63bb4038409.jpeg
tags: app-development, flutter, table, flutter-widgets

---

Flutter provides a number of widgets for displaying data in a table format, including the **Table** and **DataTable** widgets. The **Table** widget is a more flexible option than the **DataTable** widget, as it allows you to resize the rows dynamically based on the size of the content in each row.

### DataTable vs Table:

* **The Table widget is more flexible than the DataTable widget.** The Table widget allows you to resize the rows dynamically based on the size of the content in each row. The DataTable widget, on the other hand, tries to create a table with equally sized rows.
    
* **The DataTable widget has more built-in features than the Table widget.** The DataTable widget includes features such as sorting, filtering, and editing of data. The Table widget does not have these features built-in, but you can add them yourself.
    

To create a custom table using the **Table** widget, you first need to create a list of TableRows. Each **TableRow** contains a list of widgets that will be displayed in the row. The following code shows an example of a simple table with three columns:

```dart
import 'package:flutter/material.dart';

class TableExample extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Table(
      border: TableBorder.all(color: Colors.black),
      children: [
        TableRow(
          children: [
            Text('Column 1'),
            Text('Column 2'),
            Text('Column 3'),
          ],
        ),
        TableRow(
          children: [
            Text('Data 1'),
            Text('Data 2'),
            Text('Data 3'),
          ],
        ),
        TableRow(
          children: [
            Text('Data 4'),
            Text('Data 5'),
            Text('Data 6'),
          ],
        ),
      ],
    );
  }
}
```

The TableBorder property can be used to specify the border style for the table. The children property is a list of TableRows, and each TableRow is a list of widgets.

In addition to the TableBorder and children properties, the Table widget also has a number of other properties that you can use to customize the appearance of the table. For example, you can use the ***columnWidths*** property to specify the width of each column, and the textDirection property to specify the text direction of the table.

The Table widget is a powerful tool for creating custom tables in Flutter. By using the Table widget, you can create tables that are tailored to your specific needs.

### Dynamic column width:

```dart
Table(      
defaultColumnWidth: const IntrinsicColumnWidth(),
...
)
```

**NOTE:** You can use ***<mark>IntrinsicColumnWidth</mark>*** to make the column's width dynamic, but this is an expensive method to use according to the documentation.

I hope this blog post has helped you to understand how to use the Table widget to create custom tables in Flutter. For more information, please refer to the Flutter documentation on the Table widget: [https://api.flutter.dev/flutter/widgets/Table-class.html](https://api.flutter.dev/flutter/widgets/Table-class.html).