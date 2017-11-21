---
title: RDX | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.rdx
dev_langs: C++
helpviewer_keywords: rdx attribute
ms.assetid: ff8e4312-c1ad-4934-bdaa-86f54409651e
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d3384547f1c7648504137004ce90d0c0f41cda77
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="rdx"></a>rdx
Klucz rejestru tworzy lub modyfikuje istniejący klucz rejestru.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ rdx(   
   key,   
   valuename=NULL,   
   regtype   
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 `key`  
 Nazwa klucza do utworzenia lub otwarcia.  
  
 `valuename`(opcjonalnie)  
 Określa pole wartość do ustawienia. Jeśli wartość pola o tej nazwie nie istnieje już w kluczu, jest dodawany.  
  
 *regtype*  
 Typ dodawany klucz rejestru. Może być jedną z następujących czynności: **tekst**, **dword**, **binary**, lub `CString`.  
  
## <a name="remarks"></a>Uwagi  
 **Rdx** atrybutu C++ tworzy lub modyfikuje istniejącego klucza rejestru dla składnika modelu COM. Atrybut dodaje makro BEGIN_RDX_MAP do obiektu, który implementuje element członkowski docelowego. `RegistryDataExchange`, funkcja wprowadzonym w wyniku makro BEGIN_RDX_MAP może służyć do transferu danych między rejestru i elementy członkowskie danych  
  
 Ten atrybut może być używany w połączeniu z [coclass](../windows/coclass.md), [progid](../windows/progid.md), lub [vi_progid —](../windows/vi-progid.md) atrybuty lub innych oznacza jeden z nich.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa** lub `struct` elementu członkowskiego|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod dodaje klucz rejestru o nazwie MyValue opisujące składnik modelu COM CMyClass systemu.  
  
```  
// cpp_attr_ref_rdx.cpp  
// compile with: /LD /link /OPT:NOREF  
#define _ATL_ATTRIBUTES  
#include "atlbase.h"  
  
[module (name="MyLib")];  
  
class CMyClass {  
public:  
   CMyClass() {  
      strcpy_s(m_sz, "SomeValue");  
   }  
  
   [ rdx(key = "HKCR\\MyApp.MyApp.1", valuename = "MyValue", regtype = "text")]   
   char m_sz[256];  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty COM](../windows/com-attributes.md)   
 [registration_script —](../windows/registration-script.md)   
