---
title: ComPtr::As — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::As
dev_langs:
- C++
helpviewer_keywords:
- As method
ms.assetid: 2ad6c262-9bdb-4c59-a330-1af8bcd445cc
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8f3602e8be11fa1569117968848e60bd86f59acd
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="comptras-method"></a>ComPtr::As — Metoda
Zwraca obiekt comptr —, który reprezentuje interfejs identyfikowane przez parametr określonego szablonu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
template<typename U>  
HRESULT As(  
   _Out_ ComPtr<U>* p  
) const;  
  
template<typename U>  
HRESULT As(  
   _Out_ Details::ComPtrRef<ComPtr<U>> p  
) const;  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `U`  
 Interfejs, który ma być reprezentowane przez parametr `p`.  
  
 `p`  
 Obiekt comptr —, który reprezentuje interfejs określonej przez parametr `U`. Parametr `p` nie musi odwoływać się do bieżącego obiektu comptr —.  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy szablon jest formularz, która powinna być używana w kodzie. Drugi szablon jest wewnętrznych specjalizacji pomocnika, który obsługuje funkcje języka C++, takie jak [automatycznie](../cpp/auto-cpp.md) wpisz wnioskowanie — słowo kluczowe.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [ComPtr, klasa](../windows/comptr-class.md)