---
title: "Deklaracja indeksu właściwości | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- indexers
- default indexers
- defaults, indexers
- indexed properties, C++
ms.assetid: d898fdbc-2106-4b6a-8c5c-9f511d80fc2f
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fbd1158dce82b2cc2ae7d15e7b66d6b9058d8c85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="property-index-declaration"></a>Deklaracja indeksu właściwości
Składnia deklaracji właściwości indeksowanej został zmieniony z rozszerzeń zarządzanych dla języka C++ dla Visual C++.  
  
 Dwa podstawowe braków obsługi language rozszerzeń zarządzanych właściwości indeksowanych jest niemożność poziomie klasy Tworzenie indeksów dolnych; oznacza to, że wszystkie właściwości indeksowanych są wymagane, należy podać nazwę, a w związku z tym nie istnieje sposób, na przykład, aby zapewnić operator indeksu dolnego zarządzanych, które mogą być stosowane bezpośrednio do `Vector` lub `Matrix` klasy obiektu. Drugi mniej znaczących braków jest czy trudno wizualnie odróżnienia właściwości indeksowanej właściwości — liczba parametrów jest jedyną reakcją. Na koniec właściwości indeksowanych boryka się z tego samego problemów, jak te właściwości nieindeksowanych — metody dostępu nie są traktowane jako Atomowej jednostki, ale podzielone na poszczególnych metod.  Na przykład:  
  
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
  
 Jak widać w tym miejscu, indeksatorów różnią się tylko przez dodatkowe parametry, aby określić dwa lub pojedynczy wymiarze indeksu. W nowej składni indeksatorów można rozróżnić za nawiasu ([],) po nazwie indeksatora i wskazujący liczbę i rodzaj każdy indeks:  
  
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
  
 Aby wskazać klasa indeksatora poziomu, który można zastosować bezpośrednio do obiektów klasy w nowej składni `default` — słowo kluczowe zostanie ponownie użyty do zastąpienia dla jawna nazwa. Na przykład:  
  
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
  
 W nowej składni, gdy indeksowany wartość domyślna określona właściwość, dwa następujące nazwy są zarezerwowane: `get_Item` i `set_Item`. Jest tak, ponieważ są to nazwy podstawowej, generowane dla domyślnie indeksowanej właściwości.  
  
 Należy pamiętać, że nie żadna składnia prostego indeksu odpowiednikiem składni właściwości prostej.  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje składowych w obrębie klasy lub interfejsu (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 