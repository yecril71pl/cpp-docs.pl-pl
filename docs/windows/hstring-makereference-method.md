---
title: "HString::MakeReference — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::MakeReference
dev_langs:
- C++
ms.assetid: 9e1fd2b2-66ad-4a50-b647-a20ab10e522f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3e2eba5756f2c18830c4c8fe7e16f2751ea61ac1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="hstringmakereference-method"></a>HString::MakeReference — Metoda
Tworzy obiekt hstringreference — z parametru określonego ciągu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<unsigned int sizeDest>  
    static HStringReference MakeReference(  
              wchar_t const (&str)[ sizeDest]);  
  
    template<unsigned int sizeDest>  
    static HStringReference MakeReference(  
              wchar_t const (&str)[sizeDest],   
              unsigned int len);  
```  
  
#### <a name="parameters"></a>Parametry  
 `sizeDest`  
 Parametr szablonu, który określa rozmiar buforu hstringreference — docelowy.  
  
 `str`  
 Odwołanie do ciągu znaków dwubajtowych.  
  
 `len`  
 Maksymalna długość `str` buforu parametr do użycia w tej operacji. Jeśli `len` parametr nie jest określony, całą `str` parametr jest używany.  
  
## <a name="return-value"></a>Wartość zwracana  
 Hstringreference — obiektu, którego wartość jest taka sama jak określona `str` parametru.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [HString, klasa](../windows/hstring-class.md)