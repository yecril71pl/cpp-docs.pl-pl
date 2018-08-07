---
title: idl_quote — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.idl_quote
dev_langs:
- C++
helpviewer_keywords:
- idl_quote attribute
ms.assetid: a370e1b7-948b-4e67-9a25-58facf24e4c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 96e316add17ff45425bd51a7e32b276b234c6906
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606517"
---
# <a name="idlquote"></a>idl_quote
Umożliwia użycie konstrukcji języka IDL, które nie są obsługiwane w bieżącej wersji programu Visual C++ i mieć przekazywane do pliku .idl wygenerowany.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ idl_quote(  
   text  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *Tekst*  
 Nazwa atrybutu, który ma kompilator języka Visual C++ do przejścia do pliku .idl wygenerowany bez zwracania błędów kompilatora.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli **idl_quote —** atrybut C++ jest używany jako atrybut autonomiczny (przy użyciu średnika po zamykającym nawiasie), następnie *tekstu* zostanie umieszczony w pliku .idl scalone, ponieważ jest. Jeśli **idl_quote —** jest używana na symbol, *tekstu* znajduje się w bloku atrybutu dla tego symbolu.  
  
## <a name="example"></a>Przykład  
 W poniższym kodzie pokazano, jak można określić nieobsługiwany atrybut (przy użyciu **w**, który jest obsługiwany) oraz jak zdefiniować i zastosować konstrukcję niezdefiniowane .idl:  
  
```cpp  
// cpp_attr_ref_idl_quote.cpp  
// compile with: /LD  
#include <unknwn.h>  
[module(name="MyLibrary")];  
  
[export]  
struct MYFLOT {  
   int i;  
};  
  
[export]  
struct MYDUB {  
   int i;  
};  
  
[idl_quote("typedef union _S1_TYPE switch (long l1) U1_TYPE { case 1024: \  
struct MYFLOT f1; case 2048: struct MYDUB d2; } S1_TYPE;") ];  
  
typedef struct _S1_TYPE {   
   long l1;   
  
union {   
   MYFLOT f1; MYDUB d2; } U1_TYPE;   
} S1_TYPE;  
  
[uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA"), object]  
__interface IStatic{  
   HRESULT Func1([idl_quote("in")] int i);  
   HRESULT func( S1_TYPE* myStruct );  
};  
```  
  
 Ten kod powoduje, że MYFLOT i MYDUB i *tekstu* wpis do umieszczenia w pliku .idl wygenerowany. *Nazwa* wymusza parametr *tekstu* umieścić przed niczego, który odwołuje się do *nazwa* w pliku .idl wygenerowany. *Zależności* parametru wymusza definicje list zależności można umieścić przed *tekstu* w pliku .idl wygenerowany.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Kontekst atrybutu  
  
|||  
|-|-|  
|**Dotyczy**|Dowolne miejsce|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Oddzielne atrybuty](../windows/stand-alone-attributes.md)   