---
title: SafeCast | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: SafeCast
dev_langs: C++
helpviewer_keywords: SafeCast function
ms.assetid: 55316729-8456-403a-9f96-59d4038f67af
caps.latest.revision: "7"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 24b1d0c99ebc4ea543ef9d3fd1bc269d4874f706
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="safecast"></a>SafeCast
Rzutuje jednego typu liczby do innego typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<typename T, typename U>  
inline bool SafeCast (  
   const T From,  
   U& To  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in]`From`  
 Źródło liczbę do przekonwertowania. To musi być typu T.  
  
 [out]`To`  
 Odwołanie do nowego typu Liczba. Musi to być typ U.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli nie występują błędy; `false` w przypadku wystąpienia błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest częścią [Biblioteka SafeInt](../windows/safeint-library.md) i jest przeznaczony dla operacji rzutowania pojedynczego bez tworzenia wystąpienia [safeint — klasa](../windows/safeint-class.md).  
  
> [!NOTE]
>  Tej metody należy używać tylko w przypadku, gdy jednej operacji musi być chroniony. Jeśli istnieje wiele operacji, należy użyć `SafeInt` klasy zamiast kontaktować się z poszczególnych funkcji autonomicznych.  
  
 Aby uzyskać więcej informacji o typach szablonu T oraz U, zobacz [safeint — funkcje](../windows/safeint-functions.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** safeint.h  
  
 **Namespace:** Microsoft::Utilities  
  
## <a name="see-also"></a>Zobacz też  
 [Safeint — funkcje](../windows/safeint-functions.md)   
 [Biblioteka SafeInt](../windows/safeint-library.md)   
 [Safeint — klasa](../windows/safeint-class.md)