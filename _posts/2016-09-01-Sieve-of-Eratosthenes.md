---
layout: post
title: "Sieve of Eratosthenes"
date:   2016-10-01
desc: "Sieve of Eratosthenes"
keywords: "education"
categories: [Education]
tags: [education]
icon: fa-plane
---

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- The above 3 meta tags *must* come first in the head; any other head content must come *after* these tags -->
    <title>Sieve of Eratosthenes</title>

    <!-- Bootstrap -->
    <link href="css/bootstrap.min.css" rel="stylesheet">

    <!-- HTML5 shim and Respond.js for IE8 support of HTML5 elements and media queries -->
    <!-- WARNING: Respond.js doesn't work if you view the page via file:// -->
    <!--[if lt IE 9]>
      <script src="https://oss.maxcdn.com/html5shiv/3.7.2/html5shiv.min.js"></script>
      <script src="https://oss.maxcdn.com/respond/1.4.2/respond.min.js"></script>
    <![endif]-->

    <script>
        function sieve(n, k) {

            // шаг 1
            var arr1 = [];

            for (var i = 2; i < n + 1; i++) {
                arr1[i] = true
            }

            // шаг 2
            var p = 2;

            do {
                // шаг 3
                for (i = 2 * p; i < n + 1; i += p) {
                    arr1[i] = false;
                }

                // шаг 4
                for (i = p + 1; i < n + 1; i++) {
                    if (arr1[i]) break;
                }

                p = i;
            } while (p * p < n + 1); // шаг 5

            // шаг 6            
            for (i = 0; i < arr1.length; i++) {
                if (arr1[i]) {
                    prime1.push(i);
                }
            }

            // шаг 1
            var arr2 = [];

            for (var i = 2; i < k * n + 1; i++) {
                arr2[i] = true
            }

            // шаг 2
            var p = 2;

            do {
                // шаг 3
                for (i = 2 * p; i < k * n + 1; i += p) {
                    arr2[i] = false;
                }

                // шаг 4
                for (i = p + 1; i < k * n + 1; i++) {
                    if (arr2[i]) break;
                }

                p = i;
            } while (p * p < k * n + 1); // шаг 5

            // шаг 6            
            for (i = 0; i < arr2.length; i++) {
                if (arr2[i]) {
                    prime2.push(i);
                }
            }

            check(k);
        }
    </script>

    <script>
    function check(k) {

         for (var i = 0; i < prime1.length - 1 ; i++) {
             checkList[i] = '';
             var bool = false;
             for (var j = 0; j < prime2.length; j++) {
                 if (k * prime1[i] < prime2[j] && prime2[j] < k * prime1[i + 1]) {
                     if (bool)
                         checkList[i] += ', ';
                     checkList[i] += prime2[j].toString();
                     bool = true;
                 }
             }

             addToTableBody(i + 1, k, prime1[i], prime1[i + 1], k * prime1[i], k * prime1[i + 1], checkList[i]);
         }
     }
    </script>

    <script>
        function addToTableBody(col1, col2, col3, col4, col5, col6, col7) {

            var entry = [col1, col2, col3, col4, col5, col6, col7];

            tableContent = "<tr>";

            for (var i = 0; i < 7; i++) {
                tableContent += "<td>" + entry[i] + "</td>";
            };

            tableContent += "</tr>";

            TableBody.innerHTML += tableContent;
        };
    </script>

</head>
<body>

    <table class="table table-striped table-bordered table-hover">
        <thead>
            <tr>
                <th>№ п.п.</th>
                <th>K</th>
                <th>Pn</th>
                <th>Pn+1</th>
                <th>KPn</th>
                <th>KPn+1</th>
                <th>Простые числа в диапазоне от KРn до KРn+1</th>
            </tr>
        </thead>
        <tbody id="TableBody">
        </tbody>
    </table>


    <script>
        var prime1 = [];
        var prime2 = [];
        var checkList = [];
        sieve(+prompt('Введите max(Рn+1)', '100'), +prompt('Введите коэффициент K', '2'));
    </script>

    <!-- jQuery (necessary for Bootstrap's JavaScript plugins) -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
    <!-- Include all compiled plugins (below), or include individual files as needed -->
    <script src="js/bootstrap.min.js"></script>
</body>
</html>
```
