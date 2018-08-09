---
title: SafeDivide | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeDivide
dev_langs:
- C++
helpviewer_keywords:
- SafeDivide function
ms.assetid: b5b27484-ad6e-46b1-ba9f-1c7120dd103b
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4d7c966db1193def6479ecfd231293212bca2b1f
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018023"
---
# <a name="safedivide"></a>SafeDivide
Dzieli dwie liczby, w sposób zapewniający ochronę przed dzielenie przez zero.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
template<typename T, typename U>  
inline bool SafeDivide (  
   T t,  
   U u,  
   T& result  
) throw ();  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *t*  
 Dzielnik. To musi być typu T.  
  
 [in] *u*  
 Dzielna. Musi mieć typ U.  
  
 [out] *wynik*  
 Parametr gdzie **SafeDivide** zapisuje wynik.  
  
## <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli żaden błąd nie wystąpi; **false** w przypadku wystąpienia błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest częścią [Biblioteka SafeInt](../windows/safeint-library.md) i jest przeznaczona dla operacji dzielenia pojedynczego bez tworzenia wystąpienia obiektu [safeint — klasa](../windows/safeint-class.md).  
  
> [!NOTE]
>  Ta metoda ją stosować tylko po jednej operacji matematycznych muszą być chronione. Jeśli istnieje wiele operacji, należy użyć `SafeInt` klasy zamiast wywoływania poszczególnych funkcjami autonomicznymi.  
  
 Aby uzyskać więcej informacji na temat typów szablonu T i U zobacz [safeint — funkcje](../windows/safeint-functions.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** safeint.h  
  
 **Namespace:** Microsoft::Utilities  
  
## <a name="see-also"></a>Zobacz też  
 [Safeint — funkcje](../windows/safeint-functions.md)   
 [Biblioteka SafeInt](../windows/safeint-library.md)   
 [Safeint — klasa](../windows/safeint-class.md)   
 [SafeModulus](../windows/safemodulus.md)   
 [SafeMultiply](../windows/safemultiply.md)