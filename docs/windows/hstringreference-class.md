---
title: "Hstringreference — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HStringReference
dev_langs: C++
ms.assetid: 9bf823b1-17eb-4ac4-8c5d-27d27c7a4150
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1d09ba7fff2426f58f72b26a2c7e7681cecde8b5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="hstringreference-class"></a>HStringReference — Klasa
Reprezentuje wartość HSTRING utworzona na podstawie istniejących parametrów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
class HStringReference;  
```  
  
## <a name="remarks"></a>Uwagi  
 Okres istnienia buforu zapasowego w nowych HSTRING nie jest zarządzany przez środowisko wykonawcze systemu Windows. Obiekt wywołujący przydziela ciąg źródła w ramce stosu, aby uniknąć alokacji sterty i wyeliminować ryzyko przeciek pamięci. Ponadto metoda wywołująca musi zapewnić ciąg źródłowy pozostaje niezmieniona podczas okresu istnienia dołączonych HSTRING. Aby uzyskać więcej informacji, zobacz [funkcja WindowsCreateStringReference](http://msdn.microsoft.com/en-us/0361bb7e-da49-4289-a93e-de7aab8712ac).  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Hstringreference::hstringreference — Konstruktor](../windows/hstringreference-hstringreference-constructor.md)|Inicjuje nowe wystąpienie klasy hstringreference —.|  
  
### <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|[HStringReference::CopyTo — metoda](../windows/hstringreference-copyto-method.md)|Kopie bieżącego hstringreference — obiektu do obiektu HSTRING.|  
|[HStringReference::Get — metoda](../windows/hstringreference-get-method.md)|Pobiera wartość uchwytu HSTRING podstawowej.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[HStringReference::Operator = — Operator](../windows/hstringreference-operator-assign-operator.md)|Przenosi bieżący obiekt hstringreference — wartość innego obiektu hstringreference —.|  
|[HStringReference::Operator == — Operator](../windows/hstringreference-operator-equality-operator.md)|Wskazuje, czy dwa parametry są takie same.|  
|[HStringReference::Operator! = — Operator](../windows/hstringreference-operator-inequality-operator.md)|Wskazuje, czy dwa parametry nie są takie same.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `HStringReference`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl:: wrappers — Namespace](../windows/microsoft-wrl-wrappers-namespace.md)