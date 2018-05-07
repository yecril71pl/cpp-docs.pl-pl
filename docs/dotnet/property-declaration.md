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
ms.openlocfilehash: bc2cf76384078e579756abe653fb45fd1e97707f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="property-declaration"></a>Deklaracja właściwości
Sposób, aby zadeklarować właściwość w klasie zarządzanej został zmieniony z rozszerzeń zarządzanych dla języka C++ dla Visual C++.  
  
 W rozszerzeniach zarządzane projektowania, każdy `set` lub `get` metody dostępu właściwości jest określony jako metodę niezależne. Deklaracja każdej z metod jest prefiksem `__property` — słowo kluczowe. Nazwa metody rozpoczyna się od albo `set_` lub `get_` następuje rzeczywistą nazwą właściwości (jako widoczny dla użytkownika). W związku z tym `Vector` dostarczanie `x` koordynować `get` czy nazwę właściwości `get_x` i użytkownik może wywołać go jako `x`. Ten konwencji nazewnictwa i oddzielne specyfikacji metod faktycznie odzwierciedla podstawowej implementacji czasu wykonywania właściwości. Na przykład, w tym miejscu jest naszych `Vector` z zestawem współrzędnych właściwości:  
  
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
  
 To oddalenie funkcje związane z właściwością i wymaga od użytkownika lexically ujednolicenie skojarzone ustawia i pobiera. Ponadto jest pełne. W nowej składni, która jest przypomina języka C#, `property` — słowo kluczowe następuje typ właściwości i jego unadorned nazwy. `set` i `get` metody dostępu są umieszczane w bloku po nazwie właściwości. Należy pamiętać, że w przeciwieństwie do języka C#, określono podpis metody dostępu. Na przykład poniżej przedstawiono w powyższym przykładzie kodu przetłumaczyć nowej składni.  
  
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
  
 Jeśli metod dostępu właściwości poziomom dostępu unikatowych — takie jak `public get` i `private` lub `protected set`, może być określony jawny dostęp etykiety. Domyślny poziom dostępu do właściwości odzwierciedla z otaczającym poziom dostępu. Na przykład w powyższym definicji `Vector`, oba `get` i `set` metody są `public`. Aby `set` metody `protected` lub `private`, definicji czy zmieniony w następujący sposób:  
  
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
  
 Zakres — słowo kluczowe dostępu w właściwości rozszerza przed nawiasem zamykającym właściwości lub specyfikacji — słowo kluczowe dodatkowy dostęp. Nie dotyczy poza definicji właściwości otaczającego poziom dostępu, w którym właściwość jest zdefiniowana. W powyższym deklaracji, na przykład `Vector::dot()` jest publiczną metodę.  
  
 Zapisywanie zestawu/get właściwości trzech `Vector` współrzędne obejmuje trzy kroki:  
  
1.  deklaruje elementu członkowskiego prywatny stan odpowiedniego typu.  
  
2.  zwraca je, gdy użytkownik żąda można pobrać jej wartość.  
  
3.  Przypisuje nową wartość.  
  
 W nowej składni składni właściwości skrótu jest dostępna który automatyzuje tego wzorca użycia:  
  
```  
public ref class Vector sealed {   
public:  
   // equivalent shorthand property syntax  
   property double x;   
   property double y;  
   property double z;  
};  
```  
  
 Interesujące efektem ubocznym składni właściwości skrótu jest, że mimo że element członkowski zakulisowego stanu jest generowany przez kompilator, nie jest on dostępny w tej klasie, z wyjątkiem za pośrednictwem metody dostępu set/get.  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje członków w obrębie klasy lub interfejsu (C + +/ CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [właściwość](../windows/property-cpp-component-extensions.md)