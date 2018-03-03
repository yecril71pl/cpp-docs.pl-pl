---
title: "Hstringreference::hstringreference — Konstruktor | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference
dev_langs:
- C++
ms.assetid: 29f5fe11-3928-4f60-9861-f0894247bfcb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 398ea9403f784c30f8e015101c25b071f1d6fb29
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="hstringreferencehstringreference-constructor"></a>HStringReference::HStringReference — Konstruktor
Inicjuje nowe wystąpienie klasy hstringreference —.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template<unsigned int sizeDest>  
HStringReference(wchar_t const (&str)[ sizeDest]) throw();  
  
template<unsigned int sizeDest>  
HStringReference(wchar_t const (&str)[ sizeDest],   
                 unsigned int len) throw();  
  
HStringReference(HStringReference&& other) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `sizeDest`  
 Parametr szablonu, który określa rozmiar buforu hstringreference — docelowy.  
  
 `str`  
 Odwołanie do ciągu znaków dwubajtowych.  
  
 `len`  
 Maksymalna długość `str` buforu parametr do użycia w tej operacji. Jeśli `len` parametr nie jest określony, całą `str` parametr jest używany. Jeśli `len` jest większa niż `sizeDest`, `len` ustawiono `sizeDest`-1.  
  
 `other`  
 Inny obiekt hstringreference —.  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy Konstruktor inicjuje nowy obiekt hstringreference — taki sam rozmiar jak parametr `str`.  
  
 Drugi inicjuje konstruktora nowe hstringreference — obiekt, który specifeid rozmiar przez parametr `len`.  
  
 Trzeci Konstruktor inicjuje nowy obiekt hstringreference — wartość `other` parametr, a następnie niszczy `other` parametru.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [HStringReference, klasa](../windows/hstringreference-class.md)