---
title: Deklaracja indeksu właściwości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- indexers
- default indexers
- defaults, indexers
- indexed properties, C++
ms.assetid: d898fdbc-2106-4b6a-8c5c-9f511d80fc2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a6917742b285b3700548b54fef164d01c0594e5e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380468"
---
# <a name="property-index-declaration"></a>Deklaracja indeksu właściwości

Składnia do deklarowania indeksowana właściwość zmienił się z zarządzanych rozszerzeń dla C++ do Visual C++.

Dwa podstawowe braków o obsługę zarządzanych rozszerzeń języka właściwości indeksowanych jest niemożność poziomu klasa tworzenie indeksów dolnych; oznacza to, że wszystkie właściwości indeksowanych są wymagane, aby nadać nazwę, a związku z tym nie istnieje sposób, na przykład, aby zapewnić zarządzanych operator indeksu dolnego, które mogą być stosowane bezpośrednio do `Vector` lub `Matrix` obiektu klasy. Sekundy mniej znaczące braków jest, że trudno wizualnie odróżnienia Właściwość indeksowana właściwość — liczba parametrów jest jedyną reakcją. Na koniec właściwości indeksowanych borykają się z tych samych problemów, jak te nieindeksowanych — metody dostępu nie są traktowane jako pojedynczej Atomowej jednostki, ale podzielone na poszczególne metody.  Na przykład:

```
public __gc class Vector;
public __gc class Matrix {
   float mat[,];

public:
   __property void set_Item( int r, int c, float value);
   __property float get_Item( int r, int c );

   __property void set_Row( int r, Vector* value );
   __property Vector* get_Row( int r );
};
```

Jak widać w tym miejscu, indeksatorów różnią się tylko za dodatkowe parametry, aby określić, dwa lub pojedynczego indeksu wymiaru. W nowej składni indeksatorów są rozróżniane na podstawie nawiasu ([],) po nazwie indeksatora i wskazującą liczbę i typ każdego indeksu:

```
public ref class Vector {};
public ref class Matrix {
private:
   array<float, 2>^ mat;

public:
   property float Item [int,int] {
      float get( int r, int c );
      void set( int r, int c, float value );
   }

   property Vector^ Row [int] {
      Vector^ get( int r );
      void set( int r, Vector^ value );
   }
};
```

Aby wskazać, klasa indeksatora poziomu, które można stosować bezpośrednio do obiektów klasy w nowej składni `default` — słowo kluczowe zostanie ponownie użyty do podstawienia w jawnej nazwy. Na przykład:

```
public ref class Matrix {
private:
   array<float, 2>^ mat;

public:
   // ok: class level indexer now
   //
   //     Matrix mat;
   //     mat[ 0, 0 ] = 1;
   //
   // invokes the set accessor of the default indexer

   property float default [int,int] {
      float get( int r, int c );
      void set( int r, int c, float value );
   }

   property Vector^ Row [int] {
      Vector^ get( int r );
      void set( int r, Vector^ value );
   }
};
```

W nowej składni po domyślnie indeksowana właściwość zostanie określona, dwa następujące nazwy są zarezerwowane: `get_Item` i `set_Item`. Jest tak, ponieważ są to nazwy podstawowej, wygenerowany domyślnie indeksowanej właściwości.

Należy pamiętać, że nie ma prostego indeksu składni analogiczne do składni właściwości prostej.

## <a name="see-also"></a>Zobacz też

[Deklaracje składowych w obrębie klasy lub interfejsu (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)
