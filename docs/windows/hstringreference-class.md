---
title: HStringReference, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference
dev_langs:
- C++
ms.assetid: 9bf823b1-17eb-4ac4-8c5d-27d27c7a4150
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 14ad6e511baa4c7b61a2205311bfb9ea4322a5b1
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605103"
---
# <a name="hstringreference-class"></a>HStringReference — Klasa
Reprezentuje HSTRING, utworzony na podstawie istniejącego ciągu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
class HStringReference;  
```  
  
## <a name="remarks"></a>Uwagi  
 Okres istnienia buforu zapasowego w nowym obiekcie HSTRING nie jest zarządzane przez środowisko wykonawcze Windows. Obiekt wywołujący przydziela ciąg źródłowy ramce stosu, aby uniknąć alokacji stosu i wyeliminować ryzyko przecieku pamięci. Ponadto wywołujący musi zapewnić, że ciąg źródłowy pozostaje niezmieniony w czasie użytkowania dołączonego HSTRING. Aby uzyskać więcej informacji, zobacz [funkcja WindowsCreateStringReference](http://msdn.microsoft.com/0361bb7e-da49-4289-a93e-de7aab8712ac).  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[HStringReference::HStringReference, konstruktor](../windows/hstringreference-hstringreference-constructor.md)|Inicjuje nowe wystąpienie klasy **HStringReference** klasy.|  
  
### <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|[HStringReference::CopyTo, metoda](../windows/hstringreference-copyto-method.md)|Kopiuje bieżący **HStringReference** obiektu do obiektu HSTRING.|  
|[HStringReference::Get, metoda](../windows/hstringreference-get-method.md)|Pobiera wartość podstawowego dojścia HSTRING.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[HStringReference::Operator=, operator](../windows/hstringreference-operator-assign-operator.md)|Przenosi wartość innego **HStringReference** obiekt do bieżącego **HStringReference** obiektu.|  
|[HStringReference::Operator==, operator](../windows/hstringreference-operator-equality-operator.md)|Wskazuje, czy dwa parametry są równe.|  
|[HStringReference::Operator!=, operator](../windows/hstringreference-operator-inequality-operator.md)|Wskazuje, czy dwa parametry nie są równe.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `HStringReference`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers, przestrzeń nazw](../windows/microsoft-wrl-wrappers-namespace.md)