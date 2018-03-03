---
title: Delegaci i zdarzenia | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- __event keyword [C++]
- delegate keyword [C++]
- delegates [C++], upgrading from Managed Extensions for C++
- __delegate keyword
- events [C++], upgrading from Managed Extensions for C++
- event keyword [C++]
ms.assetid: 3505c626-7e5f-4492-a947-0e2248f7b84a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e332c24d30d0439705b6be5e0748518f6537478d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="delegates-and-events"></a>Delegaci i zdarzenia
Sposób, aby zadeklarować delegaci i zdarzenia został zmieniony z rozszerzeń zarządzanych dla języka C++ dla Visual C++.  
  
 Podwójne podkreślenie nie jest już potrzebne, jak pokazano w poniższym przykładzie. Przykładowy kod w zarządzanych rozszerzeń tutaj:  
  
```  
__delegate void ClickEventHandler(int, double);  
__delegate void DblClickEventHandler(String*);  
  
__gc class EventSource {  
   __event ClickEventHandler* OnClick;    
   __event DblClickEventHandler* OnDblClick;    
};  
```  
  
 Ten sam kod w nowej składni wygląda następująco:  
  
```  
delegate void ClickEventHandler( int, double );  
delegate void DblClickEventHandler( String^ );  
  
ref class EventSource {  
   event ClickEventHandler^ OnClick;   
   event DblClickEventHandler^ OnDblClick;   
};  
```  
  
 Zdarzenia (i delegatów) są typów referencyjnych, czyli w nowej składni z powodu użycia hat (`^`).  Zdarzenia obsługują składni jawnej deklaracji i mają trivial postać pokazaną w powyższym kodzie. W formularzu jawne użytkownik określi `add`, `raise`, i `remove` metody skojarzone ze zdarzeniem. (Tylko `add` i `remove` metody są wymagane; `raise` jest opcjonalne.)  
  
 W obszarze rozszerzeń zarządzanych, jeśli podasz tych metod, nie zostaną również deklaracji zdarzenia jawne, ale musi określić nazwę zdarzenia, które nie jest obecny. Każda metoda jest określone w formie `add_EventName`, `raise_EventName`, i `remove_EventName`, jak w poniższym przykładzie pobierana z specyfikacji rozszerzeń zarządzanych:  
  
```  
// explicit implementations of add, remove, raise  
public __delegate void f(int);  
public __gc struct E {  
   f* _E;  
public:  
   E() { _E = 0; }  
  
   __event void add_E1(f* d) { _E += d; }  
  
   static void Go() {  
      E* pE = new E;  
      pE->E1 += new f(pE, &E::handler);  
      pE->E1(17);   
      pE->E1 -= new f(pE, &E::handler);  
      pE->E1(17);   
   }  
  
private:  
   __event void raise_E1(int i) {  
      if (_E)  
         _E(i);  
   }  
  
protected:  
   __event void remove_E1(f* d) {  
      _E -= d;  
   }  
};  
```  
  
 Nowej składni upraszcza deklaracji, jak przedstawiono następujące tłumaczenia. Zdarzenie określa dwa lub trzy metody ujęta w parze nawiasy i umieścić bezpośrednio po deklaracji zdarzenia i jego typ delegowany skojarzony, jak pokazano poniżej:  
  
```  
public delegate void f( int );  
public ref struct E {  
private:  
   f^ _E; // delegates are also reference types  
  
public:  
   E() {  // note the replacement of 0 with nullptr!  
      _E = nullptr;   
   }  
  
   // the new aggregate syntax of an explicit event declaration  
   event f^ E1 {  
   public:  
      void add( f^ d ) {  
         _E += d;  
      }  
  
   protected:  
      void remove( f^ d ) {  
         _E -= d;  
      }  
  
   private:  
      void raise( int i ) {  
         if ( _E )  
            _E( i );  
      }  
   }  
  
   static void Go() {  
      E^ pE = gcnew E;  
      pE->E1 += gcnew f( pE, &E::handler );  
      pE->E1( 17 );   
      pE->E1 -= gcnew f( pE, &E::handler );  
      pE->E1( 17 );   
   }  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje członków w obrębie klasy lub interfejsu (C + +/ CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [Delegat (C++ Component Extensions)](../windows/delegate-cpp-component-extensions.md)   
 [event](../windows/event-cpp-component-extensions.md)