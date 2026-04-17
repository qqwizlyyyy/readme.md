# readme.md
<?php
    $conn = new mysqli("localhost","root","","spital_1d");
?>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
        <style>
        table{
           border-collapse: collapse;
        }
        td, th{
            border: 1px solid black;
        }
    </style>
</head>
<body>
    <table>
        <tr>
            <th>id_pacjenta</th>
            <th>imie</th>
            <th>nazwisko</th>
            <th>pesel</th>
            <th>data_urodzenia</th>
        </tr>
        <?php  
            $conn = new mysqli("localhost","root","","spital_1d");
            $sql = "SELECT * FROM pacjenci WHERE data_urodzenia >= \"1990-01-01\" ";
            $result = $conn->query($sql);
            while($row = $result->fetch_row()){
                echo
                "
                <tr>
                    <td>{$row[0]}</td>
                    <td>{$row[1]}</td>
                    <td>{$row[2]}</td>
                    <td>{$row[3]}</td>
                    <td>{$row[4]}</td>
                </tr>
                ";
            }
        ?>
            
</body>
</html>
<?php
    $conn -> close();
?>
Wykonałem stronę w PHP, która łączy się z bazą danych MySQL o nazwie spital_1d przy użyciu klasy mysqli. Następnie stworzyłem zapytanie SQL, które pobiera wszystkie rekordy z tabeli pacjenci, dla których data urodzenia jest równa lub późniejsza niż 1 stycznia 1990 roku.

Wyniki zapytania zapisałem w zmiennej $result, a następnie za pomocą pętli while i metody fetch_row() wyświetliłem każdy rekord w formie tabeli HTML. Każdy wiersz tabeli zawiera dane pacjenta: id, imię, nazwisko, PESEL oraz datę urodzenia.

Na końcu zamknąłem połączenie z bazą danych przy użyciu $conn->close().

Dodatkowo zastosowałem prosty styl CSS, aby tabela miała widoczne obramowania.
