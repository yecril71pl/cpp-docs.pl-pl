---
title: "_com_ptr_t — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_ptr_t
dev_langs: C++
helpviewer_keywords: _com_ptr_t class
ms.assetid: 3753a8a0-03d4-4cfd-8a9a-74872ea53971
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d395b6981e167bf759e0e26577dca962632a22c3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="comptrt-class"></a>_com_ptr_t — Klasa
**Dotyczące firmy Microsoft**  
  
 A `_com_ptr_t` obiekt hermetyzuje wskaźnika interfejsu COM i nosi nazwę "inteligentne" wskaźnik. Ta klasa szablonu zarządza alokacji zasobów i dezalokacji za pośrednictwem wywołania funkcji **IUnknown** funkcji elementów członkowskich: `QueryInterface`, `AddRef`, i **wersji**.  
  
 Wskaźnika inteligentnego jest zwykle przywołany przez definicję typedef dostarczonych przez **_COM_SMARTPTR_TYPEDEF** makra. To makro przyjmuje nazwę interfejsu i uzyskanie identyfikatora IID i deklaruje specjalizacji `_com_ptr_t` z nazwą interfejsu z dodanym sufiksem z `Ptr`. Na przykład:  
  
```  
_COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));  
```  
  
 deklaruje `_com_ptr_t` specjalizacji **IMyInterfacePtr**.  
  
 Zestaw [funkcji szablony](../cpp/relational-function-templates.md), nie jest członkiem tego szablonu klasy porównania pomocy technicznej za pomocą wskaźnika inteligentnego po prawej stronie operatora porównania.  
  
### <a name="construction"></a>Konstrukcji  
  
|||  
|-|-|  
|[_com_ptr_t —](../cpp/com-ptr-t-com-ptr-t.md)|Konstruuje `_com_ptr_t` obiektu.|  
  
### <a name="low-level-operations"></a>Operacje na niskim poziomie  
  
|||  
|-|-|  
|[AddRef](../cpp/com-ptr-t-addref.md)|Wywołania `AddRef` funkcji członkowskiej klasy **IUnknown** na wskaźnik hermetyzowany interfejsu.|  
|[Dołącz](../cpp/com-ptr-t-attach.md)|Hermetyzuje wskaźnik interfejsu pierwotnego, typu wskaźnika inteligentnego.|  
|[CreateInstance](../cpp/com-ptr-t-createinstance.md)|Tworzy nowe wystąpienie obiektu podane **CLSID** lub **ProgID**.|  
|[Odłączanie](../cpp/com-ptr-t-detach.md)|Wyodrębnia i zwraca wskaźnik hermetyzowany interfejsu.|  
|[GetActiveObject](../cpp/com-ptr-t-getactiveobject.md)|Dołącza do istniejącego wystąpienia obiektu podane **CLSID** lub **ProgID**.|  
|[GetInterfacePtr](../cpp/com-ptr-t-getinterfaceptr.md)|Zwraca wskaźnik hermetyzowany interfejsu.|  
|[QueryInterface](../cpp/com-ptr-t-queryinterface.md)|Wywołania `QueryInterface` funkcji członkowskiej klasy **IUnknown** na wskaźnik hermetyzowany interfejsu.|  
|[Wersja](../cpp/com-ptr-t-release.md)|Wywołania **wersji** funkcji członkowskiej klasy **IUnknown** na wskaźnik hermetyzowany interfejsu.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator =](../cpp/com-ptr-t-operator-equal.md)|Przypisuje nową wartość do istniejącej `_com_ptr_t` obiektu.|  
|[operatory ==,! =, \<, >, \<=, > =](../cpp/com-ptr-t-relational-operators.md)|Porównuje obiekt wskaźnika inteligentnego do innego wskaźnika inteligentnego wskaźnik interfejsu pierwotnego, lub **NULL**.|  
|[Ekstraktory](../cpp/com-ptr-t-extractors.md)|Wyodrębnij hermetyzowany wskaźnika interfejsu COM.|  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** comip.h  
  
 **Lib:** comsuppw.lib lub comsuppwd.lib (zobacz [/Zc: wchar_t (wchar_t jest typem natywnym)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) Aby uzyskać więcej informacji)  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator klas obsługi COM](../cpp/compiler-com-support-classes.md)