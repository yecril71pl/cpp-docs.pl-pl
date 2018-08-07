---
title: HStringReference::HStringReference, Konstruktor | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference
dev_langs:
- C++
ms.assetid: 29f5fe11-3928-4f60-9861-f0894247bfcb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7dce8c6fca14ad26665bf4868681234374c20f85
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39608147"
---
# <a name="hstringreferencehstringreference-constructor"></a>HStringReference::HStringReference — Konstruktor
Inicjuje nowe wystąpienie klasy **HStringReference** klasy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template<unsigned int sizeDest>  
HStringReference(wchar_t const (&str)[ sizeDest]) throw();  
  
template<unsigned int sizeDest>  
HStringReference(wchar_t const (&str)[ sizeDest],   
                 unsigned int len) throw();  
  
HStringReference(HStringReference&& other) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 *sizeDest*  
 Parametr szablonu, który określa rozmiar docelowy **HStringReference** buforu.  
  
 *str*  
 Odwołanie do ciągu znaków dwubajtowych.  
  
 *Len*  
 Maksymalna długość *str* bufora parametru w tej operacji. Jeśli *len* parametr nie jest określony, całą *str* parametr jest używany. Jeśli *len* jest większa niż *sizeDest*, *len* ustawiono *sizeDest*-1.  
  
 *other*  
 Inny **HStringReference** obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy Konstruktor inicjuje nową **HStringReference** obiekt, który jest taki sam rozmiar jak parametr *str*.  
  
 Inicjuje nowe wystąpienie drugi Konstruktor **HStringReference** obiekt specifeid rozmiaru za pomocą parametru *len*.  
  
 Trzeci Konstruktor inicjuje nowe **HStringReference** obiektu do wartości *innych* parametru, a następnie niszczy *innych* parametru.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers  
  
## <a name="see-also"></a>Zobacz też  
 [HStringReference, klasa](../windows/hstringreference-class.md)