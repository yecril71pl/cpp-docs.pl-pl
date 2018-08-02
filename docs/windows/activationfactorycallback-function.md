---
title: Activationfactorycallback — funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::ActivationFactoryCallback
dev_langs:
- C++
helpviewer_keywords:
- ActivationFactoryCallback function
ms.assetid: dd40c79b-1273-4f2a-8c24-ae9926fb4fd9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9e2e7b2301ae4dd38a40bdf4583e963e55a8b12d
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461396"
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
 *activationid —*  
 Obsługa na ciąg, który określa nazwę klasy środowiska uruchomieniowego.  
  
 *ppFactory*  
 Po zakończeniu tej operacji, fabryką aktywacji, który odpowiada parametrowi *activationid —*.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, który opisuje błąd. Prawdopodobnie niepowodzenie HRESULTs są CLASS_E_CLASSNOTAVAILABLE i E_INVALIDARG.  
  
## <a name="remarks"></a>Uwagi  
 Pobiera fabrykę aktywacji dla identyfikatora określonego aktywacji.  
  
 Środowisko wykonawcze Windows wywołuje tę funkcję wywołania zwrotnego, aby zażądać obiektu określonego przez nazwę klasy środowiska uruchomieniowego.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** module.h  
  
 **Namespace:** Microsoft::wrl:: details  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)