---
title: Hstring — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
dev_langs:
- C++
ms.assetid: 6709dd2e-8d72-4675-8ec7-1baa7d71854d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8544a78fdbdab19f44081853f5f5878f980cec01
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879375"
---
# <a name="hstring-class"></a>HString — Klasa
Klasa pomocnicza do zarządzania przez czas ich istnienia HSTRING przy użyciu wzorca RAII.
  
## <a name="syntax"></a>Składnia  
  
```cpp  
class HString;  
```  
  
## <a name="remarks"></a>Uwagi  
 Środowisko wykonawcze systemu Windows zapewnia dostęp do ciągów za pomocą dojścia HSTRING. Hstring — klasa udostępnia funkcje wygodne i operatory uprościć przy użyciu dojścia HSTRING. Ta klasa może obsłużyć HSTRING jest właścicielem za pomocą wzorca RAII przez czas ich istnienia. 
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[HString::HString, konstruktor](../windows/hstring-hstring-constructor.md)|Inicjuje nowe wystąpienie klasy HString.|  
|[HString::~HString, destruktor](../windows/hstring-tilde-hstring-destructor.md)|Niszczy bieżące wystąpienie klasy HString.|  
  
### <a name="members"></a>Elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[HString::Set, metoda](../windows/hstring-set-method.md)|Ustawia wartość bieżącego obiektu hstring — określony ciąg znaków dwubajtowych lub parametr HString.|  
|[HString::Attach, metoda](../windows/hstring-attach-method.md)|Kojarzy dany obiekt HString z bieżącym obiektem HString.|  
|[HString::CopyTo, metoda](../windows/hstring-copyto-method.md)|Kopie HString bieżącego obiektu do obiektu HSTRING.|  
|[HString::Detach, metoda](../windows/hstring-detach-method.md)|Usuwa skojarzenie określonego obiektu HString od wartości podstawowej.|  
|[HString::GetAddressOf, metoda](../windows/hstring-getaddressof-method.md)|Pobiera wskaźnik do podstawowego dojście HSTRING.|  
|[HString::Get, metoda](../windows/hstring-get-method.md)|Pobiera wartość uchwytu HSTRING podstawowej.|  
|[HString::Release, metoda](../windows/hstring-release-method.md)|Usuwa wartość ciągu podstawowej i intializes bieżącego obiektu HString wartość pustą.|  
|[HString::MakeReference, metoda](../windows/hstring-makereference-method.md)|Tworzy obiekt hstringreference — z parametru określonego ciągu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Operator HString::Operator=](../windows/hstring-operator-assign-operator.md)|Przenosi bieżący obiekt HString wartość innego obiektu HString.|  
|[Operator HString::Operator==](../windows/hstring-operator-equality-operator.md)|Wskazuje, czy dwa parametry są takie same.|  
|[Operator HString::Operator!=](../windows/hstring-operator-inequality-operator.md)|Wskazuje, czy dwa parametry nie są takie same.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `HString`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers, przestrzeń nazw](../windows/microsoft-wrl-wrappers-namespace.md)