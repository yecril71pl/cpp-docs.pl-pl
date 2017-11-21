---
title: "Activationfactorycallback — funkcja | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Details::ActivationFactoryCallback
dev_langs: C++
helpviewer_keywords: ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: adf41c8a518b0ca57326da1dd71c1a8ddd6f0a27
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="activationfactorycallback-function"></a>ActivationFactoryCallback — Funkcja
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
inline HRESULT STDAPICALLTYPE ActivationFactoryCallback(  
   HSTRING activationId,  
   IActivationFactory **ppFactory  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `activationId`  
 Dojście do ciąg określający nazwę klasy środowiska wykonawczego.  
  
 `ppFactory`  
 Po zakończeniu tej operacji, fabryki aktywacji, który odpowiada parametrowi `activationId`.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT opisujący błąd. Błąd prawdopodobnie wyników HRESULT są CLASS_E_CLASSNOTAVAILABLE i E_INVALIDARG.  
  
## <a name="remarks"></a>Uwagi  
 Pobiera fabryki aktywacji dla aktywacji określonego identyfikatora.  
  
 Środowisko wykonawcze systemu Windows Wywołanie tej funkcji wywołania zwrotnego, aby zażądać obiekt określony przez jego nazwa klasy środowiska uruchomieniowego.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl:: details — Namespace](../windows/microsoft-wrl-details-namespace.md)