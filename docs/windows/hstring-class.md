---
title: Klasa HString | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 868d0a4e2d84add447c95bfcd9690c8a17850718
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2018
ms.locfileid: "39571454"
---
# <a name="hstring-class"></a>HString — Klasa
Klasa pomocnicza do zarządzania okresem istnienia HSTRING przy użyciu wzorca RAII.
  
## <a name="syntax"></a>Składnia  
  
```cpp  
class HString;  
```  
  
## <a name="remarks"></a>Uwagi  
 Środowisko wykonawcze Windows zapewnia dostęp do ciągów za poprzez dojścia HSTRING. **HString** klasa oferuje wygodne funkcje i operatory upraszczające korzystanie z dojść HSTRING. Ta klasa może obsługiwać okres istnienia HSTRING, jest ona właścicielem za pośrednictwem wzór RAII. 
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[HString::HString, konstruktor](../windows/hstring-hstring-constructor.md)|Inicjuje nowe wystąpienie klasy **HString** klasy.|  
|[HString::~HString, destruktor](../windows/hstring-tilde-hstring-destructor.md)|Likwiduje bieżące wystąpienie **HString** klasy.|  
  
### <a name="members"></a>Elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[HString::Set, metoda](../windows/hstring-set-method.md)|Ustawia wartość bieżącego **HString** obiekt określony ciąg znaków dwubajtowych lub **HString** parametru.|  
|[HString::Attach, metoda](../windows/hstring-attach-method.md)|Kojarzy określonego **HString** obiekt z bieżącego **HString** obiektu.|  
|[HString::CopyTo, metoda](../windows/hstring-copyto-method.md)|Kopiuje bieżący **HString** obiektu do obiektu HSTRING.|  
|[HString::Detach, metoda](../windows/hstring-detach-method.md)|Powoduje usunięcie określonego **HString** obiekt z jego podstawową wartość.|  
|[HString::GetAddressOf, metoda](../windows/hstring-getaddressof-method.md)|Pobiera wskaźnik do podstawowego dojścia HSTRING.|  
|[HString::Get, metoda](../windows/hstring-get-method.md)|Pobiera wartość podstawowego dojścia HSTRING.|  
|[HString::Release, metoda](../windows/hstring-release-method.md)|Usuwa wartość ciągu i aktywuje bieżący **HString** obiektu na wartość pustą.|  
|[HString::MakeReference, metoda](../windows/hstring-makereference-method.md)|Tworzy `HStringReference` obiekt z określonego parametru ciągu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Operator HString::Operator=](../windows/hstring-operator-assign-operator.md)|Przenosi wartość innego **HString** obiekt do bieżącego **HString** obiektu.|  
|[Operator HString::Operator==](../windows/hstring-operator-equality-operator.md)|Wskazuje, czy dwa parametry są równe.|  
|[Operator HString::Operator!=](../windows/hstring-operator-inequality-operator.md)|Wskazuje, czy dwa parametry nie są równe.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `HString`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Wrappers, przestrzeń nazw](../windows/microsoft-wrl-wrappers-namespace.md)