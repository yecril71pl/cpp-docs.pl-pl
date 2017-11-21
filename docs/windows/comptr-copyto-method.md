---
title: "ComPtr::CopyTo — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr::CopyTo
dev_langs: C++
helpviewer_keywords: CopyTo method
ms.assetid: 8801bc49-6db4-4393-a55f-a701ae3b8718
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 184abddec5099eff20f75531fe240886841e9814
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="comptrcopyto-method"></a>ComPtr::CopyTo — Metoda
Kopie interfejsu bieżąca lub określona skojarzone z tego comptr — do określonego wskaźnika.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CopyTo(  
   _Deref_out_ InterfaceType** ptr  
);  
  
HRESULT CopyTo(  
   REFIID riid,  
   _Deref_out_ void** ptr  
) const;  
template<  
   typename U  
>  
  
HRESULT CopyTo(  
   _Deref_out_ U** ptr  
) const;  
```  
  
#### <a name="parameters"></a>Parametry  
 `U`  
 Nazwa typu.  
  
 `ptr`  
 Po tej operacji zakończeniu wskaźnik do żądanego interfejsu.  
  
 `riid`  
 Identyfikatora interfejsu.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT wskazującą na to, dlaczego niejawne Operacja QueryInterface nie powiodła się.  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy funkcja zwraca kopię wskaźnik skojarzony z tym comptr — interfejs. Ta funkcja zawsze zwraca wartość S_OK.  
  
 Druga funkcja wykonuje operację QueryInterface na skojarzony z tym comptr — dla interfejsu określonego przez interfejs `riid` parametru.  
  
 Trzeci funkcja wykonuje operację QueryInterface w interfejsie skojarzone z tym comptr — dla podstawowej interfejsu `U` parametru.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Comptr — klasa](../windows/comptr-class.md)