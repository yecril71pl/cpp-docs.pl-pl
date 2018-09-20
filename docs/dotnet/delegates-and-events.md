---
title: Delegaci i zdarzenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 26b67cdce8d52cba7d02f182f0582e20d0303c33
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373311"
---
# <a name="delegates-and-events"></a>Delegaci i zdarzenia

Sposób, aby zadeklarować delegaci i zdarzenia zmienił się z zarządzanych rozszerzeń dla C++ do Visual C++.

Podwójnego podkreślenia nie jest potrzebna, jak pokazano w następującym przykładzie. Oto przykładowy kod w zarządzanych rozszerzeń:

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

Zdarzenia (i delegaci) są typami odwołań, który jest otwartym w nowej składni z powodu użycia hat (`^`).  Zdarzenia obsługują składni jawnej deklaracji i prosta formularza, jak pokazano w poprzednim kodzie. W formularzu jawne użytkownik Określa `add`, `raise`, i `remove` metody skojarzone ze zdarzeniem. (Tylko `add` i `remove` metody są wymagane; `raise` jest opcjonalne.)

Jeśli podasz te metody, w ramach zarządzanych rozszerzeń nie udostępniają deklaracji jawne zdarzenia, ale musi określić nazwę zdarzenia, który nie jest obecny. Każda metoda jest określony w formie `add_EventName`, `raise_EventName`, i `remove_EventName`, jak w poniższym przykładzie pobierana z specyfikacji zarządzanych rozszerzeń:

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

Nowa składnia upraszcza deklaracji, tak jak pokazano w poniższej tłumaczenia. Określa zdarzenie, dwa lub trzy metody ujęte w parę nawiasów klamrowych i umieszczane bezpośrednio po deklaracji zdarzenia i jego typ delegata skojarzonego, jak pokazano poniżej:

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

[Deklaracje składowych w obrębie klasy lub interfejsu (C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
[delegate (C++ Component Extensions)](../windows/delegate-cpp-component-extensions.md)<br/>
[event](../windows/event-cpp-component-extensions.md)