---
title: Korzystanie z operatorów wstawiania i formatu kontrolującego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- insertion operators
ms.assetid: cdefe986-6548-4cd1-8a67-b431d7d36a1c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 51754b2b777523593118b0b0a88dfa4ac8803b20
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959810"
---
# <a name="using-insertion-operators-and-controlling-format"></a>Korzystanie z operatorów wstawiania i formatu kontrolującego

W tym temacie pokazano, jak kontrolować format oraz sposób tworzenia operatorów wstawiania dla własnych klas. Wstawianie (**<<**) operatora, który jest wcześniej zaplanowane dla wszystkich standardowych typów danych języka C++, wysyła bajtów do obiektu strumienia wyjściowego. Operatory wstawienia współpracować z wstępnie zdefiniowanych "manipulatory,", które są elementami, które Zmienianie domyślnego formatu argumenty liczby całkowitej.

Można kontrolować format z następujących opcji:

- [Szerokość danych wyjściowych](#vclrfoutputwidthanchor3)

- [Wyrównanie](#vclrfalignmentanchor4)

- [Precyzja](#vclrfprecisionanchor5)

- [Radix](#vclrfradixanchor6)

## <a name="vclrfoutputwidthanchor3"></a> Szerokość danych wyjściowych

Aby wyrównać dane wyjściowe, określamy szerokość dane wyjściowe dla każdego elementu, umieszczając `setw` manipulator w strumieniu lub przez wywołanie `width` funkcja elementu członkowskiego. W tym przykładzie po prawej stronie Wyrównuje wartości w kolumnie co najmniej 10 znaków:

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

Spacje wiodące są dodawane do dowolnej wartości mniej niż 10 znaków.

Aby uzupełnić pola, użyj `fill` funkcja elementu członkowskiego, który określa wartość znaku wypełnienie pól, które mają określoną szerokość. Ustawieniem domyślnym jest pusty. Do wypełnienia kolumny liczb gwiazdkami, zmodyfikować poprzedni **dla** pętli w następujący sposób:

```cpp
for (int i = 0; i <4; i++)
{
    cout.width(10);
    cout.fill('*');
    cout << values[i] << endl;
}
```

`endl` Manipulator zastępuje znak nowego wiersza (`'\n'`). Dane wyjściowe wyglądają następująco:

```Output
******1.23
*****35.36
*****653.7
***4358.24
```

Aby określić szerokości dla elementów danych, w tym samym wierszu, użyj `setw` manipulator:

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
      cout << setw( 6 )  << names[i]
           << setw( 10 ) << values[i] << endl;
}
```

`width` Składowa jest zadeklarowana w \<iostream >. Jeśli używasz `setw` lub innych manipulator z argumentami, musi zawierać \<iomanip >. W danych wyjściowych ciągi są drukowane w zakresie szerokość 6 i liczb całkowitych w polu Szerokość 10:

```Output
  Zoot      1.23
 Jimmy     35.36
    Al     653.7
  Stan   4358.24
```

Ani `setw` ani `width` obcina wartości. Jeśli sformatowane dane wyjściowe przekracza szerokość, wyświetla całą wartość, z zastrzeżeniem precyzję strumienia. Zarówno `setw` i `width` mają wpływ na następujące pole. Szerokość pola wraca do swojego zachowania domyślnego (szerokość niezbędne) po wydrukowaniu jedno pole. Jednak inne opcje formatowania strumienia obowiązują do momentu zmienione.

## <a name="vclrfalignmentanchor4"></a> Wyrównanie

Dane wyjściowe strumieni domyślny tekst wyrównany do prawej. Wyrównuj do lewej nazwy w poprzednim przykładzie i liczby do prawej, Zastąp **dla** pętli w następujący sposób:

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

Ustawiono flagę left-align przy użyciu [setiosflags](../standard-library/iomanip-functions.md#setiosflags) manipulator z `left` modułu wyliczającego. Ten moduł wyliczający jest zdefiniowany w [ios](../standard-library/basic-ios-class.md) klasy, więc musi zawierać odwołanie **ios::** prefiks. [Resetiosflags](../standard-library/iomanip-functions.md#resetiosflags) manipulator wyłącza flagę left-align. W odróżnieniu od `width` i `setw`, efekt `setiosflags` i `resetiosflags` jest nieodwracalna.

## <a name="vclrfprecisionanchor5"></a> Precyzja

Wartością domyślną precyzję zmiennoprzecinkową to sześć. Na przykład numer 3466.9768 drukuje jako 3466.98. Aby zmienić sposób, wyświetla tę wartość, należy użyć [setprecision](../standard-library/iomanip-functions.md#setprecision) manipulatora. Manipulator ma dwie flagi: [stałej](../standard-library/ios-functions.md#fixed) i [naukowych](../standard-library/ios-functions.md#scientific). Jeśli [stałej](../standard-library/ios-functions.md#fixed) ustawiono numer drukuje jako 3466.976800. Jeśli `scientific` jest ustawiony, wydrukowaniu jako 3.4669773 + 003.

Do wyświetlania liczb zmiennoprzecinkowych objętego [wyrównanie](#vclrfalignmentanchor4) przy użyciu jednej cyfry znaczące, Zastąp **dla** pętli w następujący sposób:

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

Program wyświetla tej listy:

```Output
Zoot          1
Jimmy     4e+01
Al        7e+02
Stan      4e+03
```

Aby wyeliminować notacji naukowej, Wstaw niniejszych przed **dla** Pętla:

```cpp
cout << setiosflags(ios::fixed);
```

Naprawiono notacji program drukuje z jedną cyfrę po punkcie dziesiętnym.

```Output
Zoot         1.2
Jimmy       35.4
Al         653.7
Stan      4358.2
```

Jeśli zmienisz `ios::fixed` flaga `ios::scientific`, program drukuje to:

```cpp
Zoot    1.2e+00
Jimmy   3.5e+01
Al      6.5e+02
Stan    4.4e+03
```

Ponownie program wyświetla jedną cyfrę po punkcie dziesiętnym. Jeśli `ios::fixed` lub `ios::scientific` jest ustawiona wartość dokładności pola określa liczbę cyfr po punkcie dziesiętnym. Jeśli żadna flaga jest ustawiona, wartość dokładności pola określa całkowitą liczbę cyfr znaczących. `resetiosflags` Manipulator czyści tych flag.

## <a name="vclrfradixanchor6"></a> Radix

`dec`, `oct`, I `hex` manipulatory Ustaw radix — domyślne dane wejściowe i wyjściowe. Na przykład w przypadku wstawiania `hex` manipulatora do strumienia wyjściowego obiektu poprawnie tłumaczy reprezentacji danych wewnętrznych liczb całkowitych na format szesnastkowy danych wyjściowych. Liczby są wyświetlane z cyframi do f w małych liter, gdy [wielkie](../standard-library/ios-functions.md#uppercase) flaga jest Wyczyść (ustawienie domyślne); w przeciwnym razie są wyświetlane napisane wielkimi literami. Podstawa domyślny jest `dec` (dziesiętna).

## <a name="quoted-strings-c14"></a>Ciągi w cudzysłowie (C ++ 14)

Wstawiając ciąg do strumienia, możesz łatwo pobrać te same parametry przywrócić przez wywołanie funkcji członkowskiej stringstream::str(). Jednak jeśli chcesz użyć operatora wyodrębniania do wstawienia w strumieniu do nowego ciągu w dowolnym momencie, może wystąpić nieoczekiwany wynik ponieważ >> operator domyślnie przestanie działać po napotkaniu pierwszego znaku odstępu.

```cpp
std::stringstream ss;
std::string inserted = "This is a sentence.";
std::string extracted;

ss << inserted;
ss >> extracted;

std::cout << inserted;     //  This is a sentence.
std::cout << extracted;    //  This
```

Można ręcznie przezwyciężyć takie zachowanie, ale aby obustronne konwertowanie ciągu bardziej wygodne, C ++ 14 dodaje `std::quoted` strumienia manipulator w \<iomanip >. Podczas wstawiania `quoted()` otacza ciągu ogranicznikiem (podwójny cudzysłów "" "domyślnie) i podczas wyodrębniania manipuluje strumienia, aby wyodrębnić wszystkie znaki, dopóki nie zostanie osiągnięty ogranicznika końcowego. Wszelkie osadzone cudzysłowy są poprzedzone znakiem zmiany znaczenia znakiem ucieczki ("\\\\" domyślnie).

Ograniczniki są obecne tylko w obiekcie strumienia; nie są obecne w wyodrębnionego ciągu, ale są obecne w ciągu zwracanego przez [basic_stringstream::str](../standard-library/basic-stringstream-class.md#str).

Zachowanie spacji operacje wstawiania i wyodrębniania jest niezależna od jak ciąg jest reprezentowana w kodzie, więc cudzysłowie operator przydaje się niezależnie od tego, czy ciąg wejściowy jest nieprzetworzony literał ciągu lub ciągu regularne. Ciąg wejściowy, niezależnie od jego format mogą mieć osadzone cudzysłowów, podziały wierszy, karty i tak dalej, a wszystkie te zostaną zachowane quoted() manipulator.

Aby uzyskać więcej informacji i przykłady pełnego kodu, zobacz [cytowane](../standard-library/iomanip-functions.md#quoted).

## <a name="see-also"></a>Zobacz także

[Strumienie wyjściowe](../standard-library/output-streams.md)<br/>
