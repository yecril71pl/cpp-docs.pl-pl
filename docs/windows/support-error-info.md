---
title: "support_error_info — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.support_error_info
dev_langs: C++
helpviewer_keywords: support_error_info attribute
ms.assetid: 20a2b55c-4738-4b35-a71d-e5e9c3a7e3bc
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b8fec0ff1f76485700199847615ac2d8fcf9e5eb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="supporterrorinfo"></a>support_error_info
Implementuje obsługę zwracania szczegółowe błędy.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ support_error_info(  
   error_interface=uuid  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 **error_interface**  
 Identyfikator implementujący interfejs **IErrorInfo**.  
  
## <a name="remarks"></a>Uwagi  
 **Support_error_info —** atrybutu C++ implementuje obsługę zwracania szczegółowe, kontekstowe błędów występujących obiektu docelowego do klienta. Dla obiektu do obsługi błędów, metody **IErrorInfo** interfejsu musi być implementowana przez obiekt. Aby uzyskać więcej informacji, zobacz [obsługi interfejsu IDispatch i IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md).  
  
 Dodaje atrybut [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) klasy jako klasę podstawową do obiektu docelowego. Powoduje to domyślna implementacja elementu **ISupportErrorInfo** i mogą być używane, gdy jeden interfejs generuje błędy w obiekcie.  
  
## <a name="example"></a>Przykład  
 Poniższy kod dodaje obsługę **ISupportErrorInfo** interfejsu do `CMyClass` obiektu.  
  
```  
// cpp_attr_ref_support_error_info.cpp  
// compile with: /LD  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module (name="mymod")];  
[object, uuid("f0b17d66-dc6e-4662-baaf-76758e09c878")]  
__interface IMyErrors  
{  
};  
  
[ coclass, support_error_info("IMyErrors"),  
  uuid("854dd392-bdc7-4781-8667-8757936f2a4f") ]  
class CMyClass  
{  
};  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**class**|  
|**Powtarzalne**|Tak|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty COM](../windows/com-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
