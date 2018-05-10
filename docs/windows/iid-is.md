---
title: iid_is — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.iid_is
dev_langs:
- C++
helpviewer_keywords:
- iid_is attribute
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f9ef3a14211e223b9902dc9843639d217ceaf1b3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="iidis"></a>iid_is
Określa identyfikator IID interfejsu COM wskazywana przez wskaźnik interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ iid_is(  
   "expression"  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *wyrażenie*  
 Wyrażenia języka C, który określa uzyskanie identyfikatora IID interfejsu COM wskazywana przez wskaźnik interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 **Iid_is —** atrybut C++ ma te same funkcje co [iid_is —](http://msdn.microsoft.com/library/windows/desktop/aa367044) MIDL atrybutu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia użycie **iid_is —**:  
  
```  
// cpp_attr_ref_iid_is.cpp  
// compile with: /LD  
#include "wtypes.h"  
#include "unknwn.h"  
[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IFireTabCtrl : IDispatch  
{  
   [id(1)] HRESULT CreateInstance([in] REFIID riid,[out, iid_is("riid")]   
   IUnknown ** ppvObject);  
};  
  
[module(name="ATLFIRELib")];  
```  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|Parametr interfejsu, element członkowski danych|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty parametru](../windows/parameter-attributes.md)   
