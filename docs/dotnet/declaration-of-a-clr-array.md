---
title: Deklaracja tablicy CLR | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- array keyword [C++]
ms.assetid: 36a8883c-2663-43f0-a90c-28f27035e036
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c3de17bb293e10c4e1a2287ef12b934633b1fe21
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426461"
---
# <a name="declaration-of-a-clr-array"></a>Deklaracja tablicy CLR

Składnia do deklarowania, tworzenie wystąpień i Inicjowanie tablicy zarządzanej zmienił się z zarządzanych rozszerzeń języka C++ do Visual C++.

Deklaracja obiektu tablicy CLR w zarządzanych rozszerzeń był rozszerzenie z deklaracją tablicy standardowa `__gc` umieszczono między nazwą obiektu array i jego wymiaru prawdopodobnie wypełnione przecinkami, tak jak z następującą parą — słowo kluczowe Przykłady:

```
void PrintValues( Object* myArr __gc[]);
void PrintValues( int myArr __gc[,,]);
```

To została uproszczona w nowej składni, w którym firma Microsoft użyj deklaracji szablonu przypominającej podobne do standardowej biblioteki C++ `vector` deklaracji. Pierwszy parametr określa typ elementu. Drugi parametr określa wymiar tablicy (przy użyciu wartości domyślnej 1, dlatego tylko wielu wymiarach wymagają drugi argument). Sam obiekt array jest śledzenie dojścia i dlatego należy zachować szczególną hat. Jeśli typ elementu jest również typem referencyjnym, wymaga także hat. Na przykład powyższy przykład, gdy wyrażone w nowej składni wygląda następująco:

```
void PrintValues( array<Object^>^ myArr );
void PrintValues( array<int,3>^ myArr );
```

Ponieważ śledzenie dojścia, a nie obiekt typu odwołania istnieje możliwość określenia tablicy CLR jako zwracany typ funkcji. (Z kolei go nie jest możliwe określenie natywna tablica jako zwracany typ funkcji). Składnia tego zrobić w zarządzanych rozszerzeń była nieco nieintuicyjnych. Na przykład:

```
Int32 f() [];
int GetArray() __gc[];
```

W programie Visual C++ deklaracja jest znacznie prostsze. Na przykład

```
array<Int32>^ f();
array<int>^ GetArray();
```

Inicjowanie skrót lokalnej tablicy zarządzanej jest obsługiwany w obu wersjach języka. Na przykład:

```
int GetArray() __gc[] {
   int a1 __gc[] = { 1, 2, 3, 4, 5 };
   Object* myObjArray __gc[] = {
      __box(26), __box(27), __box(28), __box(29), __box(30)
   };
   return a1;
}
```

znacznie uproszczono w nowej składni (należy pamiętać, że ponieważ opakowywanie jest niejawne w nowej składni `__box` operator zostały wyeliminowane — zobacz [typów wartości i ich zachowania (C + +/ interfejsu wiersza polecenia)](../dotnet/value-types-and-their-behaviors-cpp-cli.md) dyskusję na temat):

```
array<int>^ GetArray() {
   array<int>^ a1 = {1,2,3,4,5};
   array<Object^>^ myObjArray = {26,27,28,29,30};
   return a1;
}
```

Ponieważ tablicy typu odwołania CLR, deklaracja każdego obiektu tablicy jest śledzenie dojścia. W związku z tym należy przydzielić tablicy obiektów na stercie CLR. (Skróconą notacją ukrywa alokacji sterty zarządzanej). W tym miejscu jest jawne formularza inicjowania obiektu tablicy w ramach zarządzanych rozszerzeń:

```
Object* myArray[] = new Object*[2];
String* myMat[,] = new String*[4,4];
```

W ramach nowej składni `new` wyrażenie jest zamieniane `gcnew`. Rozmiary wymiaru są przekazywane jako parametry do `gcnew` wyrażenia w następujący sposób:

```
array<Object^>^ myArray = gcnew array<Object^>(2);
array<String^,2>^ myMat = gcnew array<String^,2>(4,4);
```

W nowej składni można wykonać listy Jawne inicjowanie `gcnew` wyrażenie; to nie jest obsługiwana w zarządzanych rozszerzeń. Na przykład:

```
// explicit initialization list following gcnew
// was not supported in Managed Extensions
array<Object^>^ myArray =
   gcnew array<Object^>(4){ 1, 1, 2, 3 };
```

## <a name="see-also"></a>Zobacz też

[Typy zarządzane (C + +/ CL)](../dotnet/managed-types-cpp-cl.md)<br/>
[Tablice](../windows/arrays-cpp-component-extensions.md)