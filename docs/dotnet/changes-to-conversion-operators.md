---
title: Zmiany operatorów konwersji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- conversion operators
- operators [C++], explicit type conversion
- type conversion, explicit conversions
- conversions, explicit
- explicit keyword [C++]
ms.assetid: 9b83925c-71b7-4bd3-ac2e-843dd7c7f184
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 03b17c5abc559289a9f85a10b9c5914b49498922
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381117"
---
# <a name="changes-to-conversion-operators"></a>Zmiany operatorów konwersji

Składnia dla operatorów konwersji zmienił się z zarządzanych rozszerzeń języka C++ do Visual C++.

Przykładem jest napisanie `op_Implicit` do określenia konwersji. Poniżej przedstawiono definicję `MyDouble` pobranych z specyfikacji języka:

```
__gc struct MyDouble {
   static MyDouble* op_Implicit( int i );
   static int op_Explicit( MyDouble* val );
   static String* op_Explicit( MyDouble* val );
};
```

To wynika z daną, liczbą całkowitą, algorytm konwersji tej liczby całkowitej do `MyDouble` są dostarczane przez `op_Implicit` operatora. Ponadto ten będzie można wykonać konwersji niejawnie przez kompilator. Podobnie, biorąc pod uwagę `MyDouble` object, dwa `op_Explicit` operatory podanie odpowiednich algorytmów konwersji obiektu do liczby całkowitej lub zarządzanej `String` jednostki. Jednak kompilator nie wykona konwersji, chyba że wyraźnie wymagane przez użytkownika.

W języku C# to wygląda w następujący sposób:

```
class MyDouble {
   public static implicit operator MyDouble( int i );
   public static explicit operator int( MyDouble val );
   public static explicit operator string( MyDouble val );
};
```

Kod C# wygląda większej C++ niż zarządzanych rozszerzeń języka C++. To nie jest w przypadku nowej składni.

Komitet ISO C++ wprowadzono słowo kluczowe `explicit`, aby uniknąć niezamierzonych konsekwencji — na przykład `Array` klasę, która przyjmuje jeden argument, zgodnie z wymiarem przeprowadzi niejawną konwersję dowolną liczbę całkowitą do `Array` obiekt, który to nie ma. Jednym ze sposobów, aby zapobiec takiej sytuacji jest idiom projekt zastępczy drugiego argumentu do konstruktora

Z drugiej strony należy nie zawiera pary konwersji podczas projektowania na typ klasy w języku C++. Najlepszy przykład tego jest to klasa standardowego ciągu. Niejawna konwersja jest konstruktorem jednego argumentu, biorąc ciąg stylu C. Jednak nie zapewnia odpowiedniej operator niejawnej konwersji — w przypadku konwertowania ciągu obiekt na ciąg stylu C, ale raczej wymaga, aby użytkownik jawnie wywołać funkcję o nazwie — w tym przypadku `c_str()`.

Tak kojarzenie zachowania niejawnej/jawnej operator konwersji (i jako zawieranie zbiór konwersje do postaci jednej deklaracji) wydaje się być ulepszenia w oryginalnym Obsługa języka C++ operatorów konwersji, które ostatecznie doprowadziły do `explicit` — słowo kluczowe. Obsługa języka Visual C++ dla operatorów konwersji następująco, czyli nieco mniej szczegółowe informacje, niż w języku C# ze względu na domyślne zachowanie operator obsługi algorytmu konwersji niejawnych aplikacji:

```
ref struct MyDouble {
public:
   static operator MyDouble^ ( int i );
   static explicit operator int ( MyDouble^ val );
   static explicit operator String^ ( MyDouble^ val );
};
```

Inna zmiana polega na to, że Konstruktor jeden argument jest traktowany tak, jakby jest zadeklarowany jako `explicit`. Oznacza to, że aby wyzwolić jego wywołań, jawnego rzutowania jest wymagane. Należy jednak pamiętać, że jeśli zdefiniowano operator jawnej konwersji nie Konstruktor jednego argumentu i zostanie wywołana.

## <a name="see-also"></a>Zobacz też

[Deklaracje składowych w obrębie klasy lub interfejsu (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)