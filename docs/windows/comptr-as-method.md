---
title: ComPtr::As, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::As
dev_langs:
- C++
helpviewer_keywords:
- As method
ms.assetid: 2ad6c262-9bdb-4c59-a330-1af8bcd445cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: debf10e3c3d7ca68bd277a32e55c21b3e8bf3421
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645428"
---
# <a name="comptras-method"></a>ComPtr::As — Metoda
Zwraca **ComPtr** obiekt, który reprezentuje interfejs identyfikowane za pomocą parametru określonego szablonu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template<typename U>  
HRESULT As(  
   _Out_ ComPtr<U>* p  
) const;  
  
template<typename U>  
HRESULT As(  
   _Out_ Details::ComPtrRef<ComPtr<U>> p  
) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *U*  
 Interfejs może być reprezentowana przez parametr *p*.  
  
 *p*  
 A **ComPtr** obiekt, który reprezentuje interfejs określony przez parametr *U*. Parametr *p* nie może odwoływać się do bieżącego **ComPtr** obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy szablon jest formularz, który należy używać w kodzie. Drugi szablon jest wewnętrznych specjalizacji pomocnika, która obsługuje funkcje języka C++, takie jak [automatycznie](../cpp/auto-cpp.md) słowem kluczowym dedukcji typu.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [ComPtr, klasa](../windows/comptr-class.md)