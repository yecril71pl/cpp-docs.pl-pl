---
title: "iid_is — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.iid_is
dev_langs: C++
helpviewer_keywords: iid_is attribute
ms.assetid: 2f9b42a9-7130-4b08-9b1e-0d5d360e10ff
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c2f4ccdf469ac41c6313626cc80e2256a50e7782
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 [Atrybuty parametrów](../windows/parameter-attributes.md)   
