---
title: MOVE — funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Move
dev_langs:
- C++
helpviewer_keywords:
- Move function
ms.assetid: c9525426-97e8-4d8c-9877-b689d8a0dc67
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8da1a3c839add5d056674896b5a3c6a32145924f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876774"
---
# <a name="move-function"></a>Move — Funkcja
Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class T>  
inline typename RemoveReference<T>::Type&& Move(  
   _Inout_ T&& arg  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ argumentu.  
  
 `arg`  
 Argument przenoszenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Parametr `arg` po cech odwołanie lub odwołanie do r-wartości, jeśli zostały usunięte.  
  
## <a name="remarks"></a>Uwagi  
 Przenosi określony argument z jednej lokalizacji.  
  
 Aby uzyskać więcej informacji, zobacz **Przenieś semantyki** sekcji [deklarator odwołania do r-wartości: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** internal.h  
  
 **Namespace:** Microsoft::wrl:: details —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)