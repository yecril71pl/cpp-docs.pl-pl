---
title: SafeNotEquals | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeNotEquals
dev_langs:
- C++
helpviewer_keywords:
- SafeNotEquals function
ms.assetid: 032e45a8-4159-4b55-b7cc-ecd27f4e4788
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 37f9627e301831c98ccab7a0c79258d96c520f1a
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605139"
---
# <a name="safenotequals"></a>SafeNotEquals
Określa, czy dwie liczby nie są równe.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename T, typename U>  
inline bool SafeNotEquals (  
   const T t,  
   const U u  
) throw ();  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *t*  
 Pierwsza liczba do porównania. To musi być typu `T`.  
  
 [in] *u*  
 Druga liczba do porównania. To musi być typu `U`.  
  
## <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli *t* i *u* nie są równe; w przeciwnym razie **false**.  
  
## <a name="remarks"></a>Uwagi  
 Rozszerza metoda `!=` ponieważ **SafeNotEquals** umożliwia porównywanie dwa różne typy liczb.  
  
 Ta metoda jest częścią [Biblioteka SafeInt](../windows/safeint-library.md) i jest przeznaczony dla operacji jedno porównanie bez tworzenia wystąpienia obiektu [safeint — klasa](../windows/safeint-class.md).  
  
> [!NOTE]
>  Ta metoda ją stosować tylko po jednej operacji matematycznych muszą być chronione. Jeśli istnieje wiele operacji, należy użyć `SafeInt` klasy zamiast wywoływania poszczególnych funkcjami autonomicznymi.  
  
 Aby uzyskać więcej informacji na temat typów szablonu `T` i `U`, zobacz [safeint — funkcje](../windows/safeint-functions.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** safeint.h  
  
 **Namespace:** Microsoft::Utilities  
  
## <a name="see-also"></a>Zobacz też  
 [Safeint — funkcje](../windows/safeint-functions.md)   
 [Biblioteka SafeInt](../windows/safeint-library.md)   
 [Safeint — klasa](../windows/safeint-class.md)   
 [SafeEquals](../windows/safeequals.md)