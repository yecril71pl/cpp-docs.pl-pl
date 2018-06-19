---
title: ComPtr::CopyTo — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::CopyTo
dev_langs:
- C++
helpviewer_keywords:
- CopyTo method
ms.assetid: 8801bc49-6db4-4393-a55f-a701ae3b8718
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 680c1278ca2b17c7ea35e72946fb5d5030c5e7c0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33870874"
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

template<typename U>  
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
 [ComPtr, klasa](../windows/comptr-class.md)