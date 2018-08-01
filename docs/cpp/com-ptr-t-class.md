---
title: _com_ptr_t — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t
dev_langs:
- C++
helpviewer_keywords:
- _com_ptr_t class
ms.assetid: 3753a8a0-03d4-4cfd-8a9a-74872ea53971
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0e9e3d7f16e40d41774dd1def89ef9bdd0ba1c82
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404600"
---
# <a name="comptrt-class"></a>_com_ptr_t — Klasa
**Microsoft Specific**  
  
 A **_com_ptr_t** obiekt hermetyzuje wskaźnika interfejsu COM i nosi nazwę "eleganckie" wskaźnik. Tej klasy szablonu zarządza alokacją i dezalokacją za pośrednictwem wywołania funkcji zasobów `IUnknown` elementów członkowskich: `QueryInterface`, `AddRef`, i `Release`.  
  
 Zazwyczaj odwołuje się w zgodnie z definicją typedef, dostarczone przez makra _COM_SMARTPTR_TYPEDEF inteligentnego wskaźnika. To makro przyjmuje nazwę interfejsu i identyfikatora IID i deklaruje specjalizacją **_com_ptr_t** nazwą interfejsu oraz sufiks `Ptr`. Na przykład:  
  
```cpp 
_COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));  
```  
  
 deklaruje **_com_ptr_t** specjalizacji `IMyInterfacePtr`.  
  
 Zbiór [funkcji szablonów](../cpp/relational-function-templates.md), niebędących członkami tego szablonu klasy pomocy technicznej porównania z wartością inteligentny wskaźnik po prawej stronie operatora porównania.  
  
### <a name="construction"></a>Konstrukcja  
  
|||  
|-|-|  
|[_com_ptr_t](../cpp/com-ptr-t-com-ptr-t.md)|Konstruuje **_com_ptr_t** obiektu.|  
  
### <a name="low-level-operations"></a>Operacje na niskim poziomie  
  
|||  
|-|-|  
|[AddRef](../cpp/com-ptr-t-addref.md)|Wywołania `AddRef` funkcji składowej typu `IUnknown` interfejsu zhermetyzowanego wskaźnika.|  
|[Attach](../cpp/com-ptr-t-attach.md)|Hermetyzuje surowego wskaźnika interfejsu tego inteligentnego wskaźnika typu.|  
|[CreateInstance](../cpp/com-ptr-t-createinstance.md)|Tworzy nowe wystąpienie obiektu, biorąc pod uwagę `CLSID` lub `ProgID`.|  
|[Detach](../cpp/com-ptr-t-detach.md)|Wyodrębnia i zwraca wskaźnik zhermetyzowany interfejs.|  
|[Getactiveobject —](../cpp/com-ptr-t-getactiveobject.md)|Dołącza do istniejącego wystąpienia danego obiektu `CLSID` lub `ProgID`.|  
|[GetInterfacePtr](../cpp/com-ptr-t-getinterfaceptr.md)|Zwraca wskaźnik zhermetyzowany interfejs.|  
|[QueryInterface](../cpp/com-ptr-t-queryinterface.md)|Wywołania `QueryInterface` funkcji składowej typu `IUnknown` interfejsu zhermetyzowanego wskaźnika.|  
|[Wersja](../cpp/com-ptr-t-release.md)|Wywołania `Release` funkcji składowej typu `IUnknown` interfejsu zhermetyzowanego wskaźnika.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator =](../cpp/com-ptr-t-operator-equal.md)|Przypisuje nową wartość do istniejącej **_com_ptr_t** obiektu.|  
|[operatory ==,! =, \<, >, \<=, > =](../cpp/com-ptr-t-relational-operators.md)|Porównuje obiekt inteligentny wskaźnik do innego wskaźnika inteligentnego, surowego wskaźnika interfejsu, lub wartość NULL.|  
|[Ekstraktory](../cpp/com-ptr-t-extractors.md)|Wyodrębnij zhermetyzowanego wskaźnika interfejsu COM.|  
  
**END specyficzny dla Microsoft**  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<comip.h >  
  
 **Lib:** comsuppw.lib lub comsuppwd.lib (zobacz [/Zc: wchar_t (wchar_t jest typem natywnym)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) Aby uzyskać więcej informacji)  
  
## <a name="see-also"></a>Zobacz także  
 [Kompilator klas obsługi COM](../cpp/compiler-com-support-classes.md)