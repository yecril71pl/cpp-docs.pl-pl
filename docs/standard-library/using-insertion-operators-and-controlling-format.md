---
title: Korzystanie z operatorów wstawiania i formatu kontrolującego
ms.date: 11/04/2016
helpviewer_keywords:
- insertion operators
ms.assetid: cdefe986-6548-4cd1-8a67-b431d7d36a1c
ms.openlocfilehash: 2cf399501c0eab32e8bee80dfcb98d870c0193cb
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458024"
---
# <a name="using-insertion-operators-and-controlling-format"></a>Korzystanie z operatorów wstawiania i formatu kontrolującego

W tym temacie pokazano, jak kontrolować format i jak tworzyć operatory wstawiania dla własnych klas. Operator Wstaw ( **<<** ), który jest zaprogramowany dla wszystkich standardowych C++ typów danych, wysyła bajty do obiektu strumienia wyjściowego. Operatory wstawiania działają ze wstępnie zdefiniowanymi "zadaniami", które są elementami, które zmieniają domyślny format argumentów liczb całkowitych.

Można kontrolować format przy użyciu następujących opcji:

- [Szerokość wyjściowa](#vclrfoutputwidthanchor3)

- [Struktury](#vclrfalignmentanchor4)

- [Dokładne](#vclrfprecisionanchor5)

- [Radix](#vclrfradixanchor6)

## <a name="vclrfoutputwidthanchor3"></a>Szerokość wyjściowa

Aby wyrównać dane wyjściowe, należy określić szerokość wyjściową dla każdego elementu `setw` , umieszczając Manipulator w strumieniu lub `width` wywołując funkcję elementu członkowskiego. Ten przykład umożliwia wyrównanie wartości w kolumnie o szerokości co najmniej 10 znaków:

```cpp
// output_width.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   double values[] = { 1.23, 35.36, 653.7, 4358.24 };
   for( int i = 0; i < 4; i++ )
   {
      cout.width(10);
      cout << values[i] << '\n';
   }
}
```

```Output
      1.23
     35.36
     653.7
   4358.24
```

Wiodące puste znaki są dodawane do dowolnej wartości mniejszej niż 10 znaków.

Aby zapełnić pole, użyj `fill` funkcji członkowskiej, która ustawia wartość znaku uzupełniania dla pól, które mają określoną szerokość. Wartość domyślna to wartość pusta. Aby przystąpić do uzupełniania kolumny liczb przy użyciu gwiazdek, zmodyfikuj poprzednią pętlę **for** w następujący sposób:

```cpp
for (int i = 0; i <4; i++)
{
    cout.width(10);
    cout.fill('*');
    cout << values[i] << endl;
}
```

Manipulator zastępuje znak nowego wiersza (`'\n'`). `endl` Dane wyjściowe wyglądają następująco:

```Output
******1.23
*****35.36
*****653.7
***4358.24
```

Aby określić szerokości dla elementów danych w tym samym wierszu, użyj `setw` Manipulator:

```cpp
// setw.cpp
// compile with: /EHsc
#include <iostream>
#include <iomanip>
using namespace std;

int main( )
{
   double values[] = { 1.23, 35.36, 653.7, 4358.24 };
   char *names[] = { "Zoot", "Jimmy", "Al", "Stan" };
   for( int i = 0; i < 4; i++ )
      cout << setw( 7 )  << names[i]
           << setw( 10 ) << values[i] << endl;
}
```

Funkcja członkowska jest zadeklarowana \<w iostream >. `width` Jeśli używasz `setw` lub dowolnego innego Manipulator z argumentami, musisz uwzględnić \<iomanip >. W danych wyjściowych ciągi są drukowane w polu o szerokości 6 i liczbie całkowitej w polu o szerokości 10:

```Output
   Zoot      1.23
  Jimmy     35.36
     Al     653.7
   Stan   4358.24
```

Ani `setw`nieobcinawartości. `width` Jeśli sformatowane dane wyjściowe przekraczają szerokość, cała wartość zostanie wydrukowany, pod warunkiem ustawienia dokładności strumienia. Oba `setw` i`width` mają wpływ tylko na następujące pola. Szerokość pola przywraca zachowanie domyślne (wymagana szerokość) po wydrukowaniu jednego pola. Jednak inne opcje formatu strumienia będą obowiązywać do momentu zmiany.

## <a name="vclrfalignmentanchor4"></a>Struktury

Strumienie wyjściowe domyślnie do tekstu wyrównanego do prawej. Aby wyrównać lewe nazwy w poprzednim przykładzie i wyrównane do prawej, Zastąp pętlę **for** w następujący sposób:

```cpp
for (int i = 0; i <4; i++)
    cout << setiosflags(ios::left)
         << setw(6) << names[i]
         << resetiosflags(ios::left)
         << setw(10) << values[i] << endl;
```

Dane wyjściowe wyglądają następująco:

```Output
Zoot        1.23
Jimmy      35.36
Al         653.7
Stan     4358.24
```

Flaga wyrównany do lewej jest ustawiana za pomocą [setiosflags](../standard-library/iomanip-functions.md#setiosflags) Manipulator z `left` modułem wyliczającym. Ten moduł wyliczający jest zdefiniowany w klasie [systemu iOS](../standard-library/basic-ios-class.md) , więc jego odwołanie musi zawierać prefiks **iOS::** . [Resetiosflags](../standard-library/iomanip-functions.md#resetiosflags) Manipulator wyłącza flagę wyrównany do lewej. W `width` przeciwieństwie `setw`do i, efekt `setiosflags` i `resetiosflags` jest trwały.

## <a name="vclrfprecisionanchor5"></a>Dokładne

Wartość domyślna dla precyzji zmiennoprzecinkowej to sześć. Na przykład numer 3466,9768 drukuje jako 3466,98. Aby zmienić sposób drukowania tej wartości, użyj metody [setprecision](../standard-library/iomanip-functions.md#setprecision) Manipulator. Manipulator ma dwie flagi: [naprawione](../standard-library/ios-functions.md#fixed) i [naukowe](../standard-library/ios-functions.md#scientific). W przypadku ustawienia opcji [stała](../standard-library/ios-functions.md#fixed) liczba jest drukowana jako 3466,976800. Jeśli `scientific` jest ustawiona, zostanie wydrukowana jako 3.4669773 + 003.

Aby wyświetlić liczby zmiennoprzecinkowe wyświetlane w wyrównaniu [](#vclrfalignmentanchor4) z jedną cyfrą znaczącą, Zastąp pętlę **for** w następujący sposób:

```cpp
for (int i = 0; i <4; i++)
    cout << setiosflags(ios::left)
         << setw(6)
         << names[i]
         << resetiosflags(ios::left)
         << setw(10)
         << setprecision(1)
         << values[i]
         << endl;
```

Program drukuje tę listę:

```Output
Zoot          1
Jimmy     4e+01
Al        7e+02
Stan      4e+03
```

Aby wyeliminować notację wykładniczą, Wstaw tę instrukcję przed pętlą **for** :

```cpp
cout << setiosflags(ios::fixed);
```

Ze stałym zapisem program drukuje z jedną cyfrą po przecinku dziesiętnym.

```Output
Zoot         1.2
Jimmy       35.4
Al         653.7
Stan      4358.2
```

Jeśli zmienisz `ios::fixed` flagę na `ios::scientific`, program drukuje:

```cpp
Zoot    1.2e+00
Jimmy   3.5e+01
Al      6.5e+02
Stan    4.4e+03
```

Ponownie program drukuje jedną cyfrę po przecinku dziesiętnym. `ios::fixed` Jeślialbojestustawiona,wartośćprecyzjiokreślaliczbęcyfrpo`ios::scientific` przecinku dziesiętnym. Jeśli flaga nie jest ustawiona, wartość precyzji określa łączną liczbę cyfr znaczących. `resetiosflags` Manipulator czyści te flagi.

## <a name="vclrfradixanchor6"></a> Radix

`dec`, ,`oct`I manipulowanieustawiadomyślny`hex` podstawy dla danych wejściowych i wyjściowych. Na przykład, Jeśli wstawisz `hex` Manipulator do strumienia danych wyjściowych, obiekt poprawnie tłumaczy wewnętrzną reprezentację danych liczb całkowitych na szesnastkowy format wyjściowy. Liczby są wyświetlane z cyframi od a do f w przypadku małych liter, jeśli flaga [wielkich](../standard-library/ios-functions.md#uppercase) liter jest wyczyszczona (wartość domyślna); w przeciwnym razie są wyświetlane w Wielkiej litery. Wartość domyślna podstawy to `dec` (Decimal).

## <a name="quoted-strings-c14"></a>Ciągi ujęte w cudzysłów (C++ 14)

Po wstawieniu ciągu do strumienia można łatwo pobrać ten sam ciąg z powrotem, wywołując funkcję członkowską stringstream —:: str (). Jeśli jednak chcesz użyć operatora wyodrębniania do wstawienia strumienia do nowego ciągu w późniejszym czasie, możesz uzyskać nieoczekiwany wynik, ponieważ operator > > domyślnie zostanie zatrzymany po napotkaniu pierwszego znaku odstępu.

```cpp
std::stringstream ss;
std::string inserted = "This is a sentence.";
std::string extracted;

ss << inserted;
ss >> extracted;

std::cout << inserted;     //  This is a sentence.
std::cout << extracted;    //  This
```

To zachowanie można przezwyciężyć ręcznie, ale w celu przeanalizowania ciągów, które jest `std::quoted` bardziej wygodne, język c++ 14 dodaje Manipulator strumienia w \<iomanip >. Po wstawieniu, `quoted()` ujmuje ciąg z ogranicznikiem (domyślnie w cudzysłowie "" ") i przy wyodrębnianiu manipuluje strumieniem, aby wyodrębnić wszystkie znaki do momentu, gdy zostanie osiągnięty końcowy ogranicznik. Wszelkie osadzone cudzysłowy są wyprowadzane z użyciem znaku ucieczki\\(\\domyślnie "").

Ograniczniki są obecne tylko w obiekcie Stream; nie występują one w wyodrębnionym ciągu, ale są obecne w ciągu zwracanym przez [basic_stringstream:: str](../standard-library/basic-stringstream-class.md#str).

Zachowanie odstępów operacji wstawiania i wyodrębniania jest niezależne od sposobu reprezentowania ciągu w kodzie, więc operator quoty jest przydatny bez względu na to, czy ciąg wejściowy jest niesformatowanym literałem ciągu czy ciągiem regularnym. Ciąg wejściowy, niezależnie od jego formatu, może zawierać osadzone cudzysłowy, podziały wierszy, karty i tak dalej. wszystkie te dane zostaną zachowane przez cytowane () Manipulator.

Aby uzyskać więcej informacji i zapoznać się z pełnymi przykładami kodu, zobacz [cytowane](../standard-library/iomanip-functions.md#quoted).

## <a name="see-also"></a>Zobacz także

[Strumienie wyjściowe](../standard-library/output-streams.md)
