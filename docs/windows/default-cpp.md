---
title: "domyślne (C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.default
dev_langs: C++
helpviewer_keywords:
- default attribute
- attributes [C#], default attribute
- defaults, default attribute
ms.assetid: 0cdca716-1ba8-46d7-9399-167e55492870
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6b24b0ed9b8e547a52388b6f93a4955da782331b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="default-c"></a>default (C++)
Wskazuje, że niestandardowe lub dispinterface zdefiniowane w obrębie klasy coclass reprezentuje domyślny interfejs programowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ default(  
   interface1,  
   interface2  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *interface1*  
 Domyślny interfejs, który zostanie udostępniona w środowiskach skryptów tworzenia obiektu oparte na klasie zdefiniowane z **domyślne** atrybutu.  
  
 Jeśli nie określono żadnych interfejsu domyślnego, pierwsze wystąpienie interfejsu nonsource jest używany jako domyślny.  
  
 *interface2*(opcjonalnie)  
 Domyślny interfejs źródłowy. Należy także określić tego interfejsu [źródła](../windows/source-cpp.md) atrybutu.  
  
 Jeśli nie określono żadnych interfejsu źródłowego domyślne, pierwszy interfejs źródłowy jest używany jako domyślny.  
  
## <a name="remarks"></a>Uwagi  
 **Domyślne** atrybut C++ ma te same funkcje co [domyślne](http://msdn.microsoft.com/library/windows/desktop/aa366787) MIDL atrybutu. **Domyślne** również jest używany atrybut [przypadku](../windows/case-cpp.md) atrybutu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób **domyślne** służy do określania, w definicji klasy coclass **ICustomDispatch** jako domyślny interfejs programowania:  
  
```  
// cpp_attr_ref_default.cpp  
// compile with: /LD  
#include "windows.h"  
[module(name="MyLibrary")];  
  
[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]  
__interface ICustom {  
   HRESULT Custom([in] long l, [out, retval] long *pLong);  
};  
  
[dual, uuid("9E66A291-4365-11D2-A997-00C04FA37DDB")]   
__interface IDual {  
   HRESULT Dual([in] long l, [out, retval] long *pLong);  
};  
  
[object, uuid("9E66A293-4365-11D2-A997-00C04FA37DDB")]  
__interface ICustomDispatch : public IDispatch {  
   HRESULT Dispatch([in] long l, [out, retval] long *pLong);  
};  
  
[   coclass,  
   default(ICustomDispatch),   
   source(IDual),  
   uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")  
]  
class CClass : public ICustom, public IDual, public ICustomDispatch {  
   HRESULT Custom(long l, long *pLong) { return(S_OK); }  
   HRESULT Dual(long l, long *pLong) { return(S_OK); }  
   HRESULT Dispatch(long l, long *pLong) { return(S_OK); }  
};  
  
int main() {  
#if 0 // Can't instantiate without implementations of IUnknown/IDispatch  
   CClass *pClass = new CClass;  
  
   long llong;  
  
   pClass->custom(1, &llong);  
   pClass->dual(1, &llong);  
   pClass->dispinterface(1, &llong);  
   pClass->dispatch(1, &llong);  
  
   delete pClass;  
#endif  
   return(0);  
}  
```  
  
 [Źródła](../windows/source-cpp.md) atrybutu zawiera również przykład sposobu użycia **domyślne**.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**, `struct`, element członkowski danych|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|**coclass** (gdy jest stosowany do **klasy** lub `struct`)|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
 [coclass](../windows/coclass.md)   
