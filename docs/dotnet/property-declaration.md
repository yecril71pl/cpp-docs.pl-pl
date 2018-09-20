---
title: Deklaracja właściwości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- __property keyword
- declaring properties, C++
- property keyword [C++]
ms.assetid: de169378-a8b8-49f4-a586-76bffc9b5c9f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 019b8eae17952bfe53fd8fbf14db4bafce1bf463
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438304"
---
# <a name="property-declaration"></a>Deklaracja właściwości

Sposób, aby zadeklarować właściwość w klasie zarządzanej zmienił się z zarządzanych rozszerzeń dla C++ do Visual C++.

W zarządzanych rozszerzeń projektowania, każdy `set` lub `get` metody dostępu właściwości jest określony jako niezależne metodę. Deklaracja każdej z metod jest poprzedzony znakiem `__property` — słowo kluczowe. Nazwa metody zaczyna się od albo `set_` lub `get_` następuje rzeczywista nazwa właściwości (jako widoczny dla użytkownika). W związku z tym `Vector` dostarczanie `x` koordynować `get` będzie nazwa właściwości `get_x` i użytkownik powodowałoby wywołanie pliku wykonywalnego jako `x`. Ten konwencji nazewnictwa i oddzielnych specyfikacji metod faktycznie odzwierciedla podstawowej implementacji środowiska uruchomieniowego właściwości. Na przykład Oto nasze `Vector` zestaw współrzędnych właściwości:

```
public __gc __sealed class Vector {
public:
   __property double get_x(){ return _x; }
   __property double get_y(){ return _y; }
   __property double get_z(){ return _z; }

   __property void set_x( double newx ){ _x = newx; }
   __property void set_y( double newy ){ _y = newy; }
   __property void set_z( double newz ){ _z = newz; }
};
```

Oddalenie funkcje związane z właściwością i wymaga od użytkownika leksykalnie ujednolicenie skojarzone zestawy i pobiera. Ponadto jest pełne. W nowej składni, która jest bardziej jak w przypadku języka C#, `property` — słowo kluczowe następuje typ właściwości i jego unadorned nazwy. `set` i `get` metody dostępu są umieszczane w bloku po nazwie właściwości. Należy pamiętać, że w przeciwieństwie do języka C#, podpis metody dostępu jest określony. Na przykład poniżej przedstawiono przykład kodu powyżej przetłumaczyć nowej składni.

```
public ref class Vector sealed {
public:
   property double x {
      double get() {
         return _x;
      }

      void set( double newx ) {
         _x = newx;
      }
   } // Note: no semi-colon
};
```

Jeśli metody dostępu właściwości odzwierciedlają poziomów dostępu unikatowych — takich jak `public get` i `private` lub `protected set`, może być określony jawny dostęp etykiety. Domyślnie poziom dostępu właściwość odzwierciedla z otaczającym poziom dostępu. Na przykład w powyższej definicji `Vector`, zarówno `get` i `set` metody są `public`. Aby `set` metoda `protected` lub `private`, definicja będzie skorygowane w następujący sposób:

```
public ref class Vector sealed {
public:
   property double x {
      double get() {
         return _x;
      }

   private:
      void set( double newx ) {
         _x = newx;
      }

   } // note: extent of private culminates here

// note: dot is a public method of Vector
double dot( const Vector^ wv );

// etc.
};
```

Rozszerza zakres dostępu słowa kluczowego, w ramach właściwości do momentu nawias zamykający właściwości lub specyfikacji — słowo kluczowe dodatkowe prawa dostępu. Nie jest rozszerzana poza definicji właściwości otaczającego poziom dostępu, w którym właściwość jest zdefiniowana. W powyższej deklaracji, na przykład `Vector::dot()` jest publiczną metodę.

Zapisywanie właściwości set/get dla trzech `Vector` współrzędne obejmuje trzy kroki:

1. deklaruje składowej prywatny stan odpowiedniego typu.

1. zwraca je, gdy użytkownik chce uzyskać jego wartość.

1. Przypisuje nową wartość.

W nowej składni oczekiwaliśmy składni właściwości jest dostępna który automatyzuje ten wzorzec użycia:

```
public ref class Vector sealed {
public:
   // equivalent shorthand property syntax
   property double x;
   property double y;
   property double z;
};
```

Interesujące efekt uboczny składni właściwość skrótowa jest, że chociaż członek stanu widoku backstage jest generowany przez kompilator, nie jest dostępna w klasie, z wyjątkiem sytuacji, za pomocą metody dostępu set/get.

## <a name="see-also"></a>Zobacz też

[Deklaracje składowych w obrębie klasy lub interfejsu (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
[właściwość](../windows/property-cpp-component-extensions.md)