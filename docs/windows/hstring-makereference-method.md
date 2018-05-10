---
title: HString::MakeReference — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::MakeReference
dev_langs:
- C++
ms.assetid: 9e1fd2b2-66ad-4a50-b647-a20ab10e522f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e30b3ea3c6b791eb654a6fbbe91b3c87353f31c1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
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