---
title: "idl_quote — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.idl_quote
dev_langs: C++
helpviewer_keywords: idl_quote attribute
ms.assetid: a370e1b7-948b-4e67-9a25-58facf24e4c9
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8ca11d9b92ba1dd0dc7f5437bf1dec812f2edfcc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
 *tekst*  
 Nazwa atrybutu, który ma kompilatora Visual C++ do przekazywania do pliku .idl wygenerowanego bez wystąpi błąd kompilatora powrotu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli **idl_quote —** atrybut C++ jest używany jako atrybut autonomiczny (średnikiem po zamykający nawias kwadratowy), następnie *tekst* znajduje się w pliku .idl scalone, jak. Jeśli **idl_quote —** jest używany na symbolu, *tekst* znajduje się w bloku atrybutu dla tego symbolu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia, jak można określić nieobsługiwany atrybut (przy użyciu **w**, która jest obsługiwana) oraz sposób definiowania i użyj konstrukcji niezdefiniowany .idl:  
  
```  
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
  
 Ten kod powoduje, że MYFLOT i MYDUB i *tekst* wpisu do umieszczenia w pliku .idl wygenerowany. *Nazwa* wymusza parametru *tekst* być umieszczone przed niczego, który odwołuje się do *nazwa* w pliku .idl wygenerowany. *Zależności* parametru wymusza definicje listy zależności, aby umieścić przed *tekst* w pliku .idl wygenerowany.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|Dowolnego miejsca|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Oddzielne atrybuty](../windows/stand-alone-attributes.md)   
