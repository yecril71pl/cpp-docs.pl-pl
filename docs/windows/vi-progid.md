---
title: "vi_progid — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.vi_progid
dev_langs: C++
helpviewer_keywords: vi_progid attribute
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f5a7560a05e670f8e6d0b04eea614be80db2ba93
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="viprogid"></a>vi_progid
Określa niezależny od wersji formularza identyfikatora ProgID.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ vi_progid(  
   name  
) ];  
```  
  
#### <a name="parameters"></a>Parametry  
 *Nazwa*  
 Identyfikator ProgID niezależny od wersji reprezentujący obiekt.  
  
 ProgID stanowi wersję identyfikator klasy (CLSID) używany do identyfikowania obiektów COM/ActiveX zrozumiałą dla użytkownika.  
  
## <a name="remarks"></a>Uwagi  
 **Vi_progid —** atrybutu C++ pozwala określić identyfikator ProgID niezależny od wersji dla obiekt COM. Identyfikator ProgID ma formę *name1.name2.version*. Nie ma ProgID niezależny od wersji *wersji*. Można określić zarówno **progid** i **vi_progid —** atrybuty klasy coclass. Jeśli nie określisz **vi_progid —**, wersji niezależne ProgID jest wartość określoną przez [progid](../windows/progid.md) atrybutu.  
  
 **vi_progid —** oznacza **coclass** atrybutu, oznacza to, że jeśli określisz **vi_progid —**, jest odpowiednikiem określenie **coclass** i **vi_progid —** atrybutów.  
  
 **Vi_progid —** atrybutu powoduje, że klasa automatycznie rejestrowana o określonej nazwie. .Idl wygenerowanego pliku nie zostanie wyświetlona wartość identyfikatora ProgID.  
  
 W projektach ATL Jeśli [coclass](../windows/coclass.md) atrybut również występuje, określony identyfikator ProgID jest używany przez **GetVersionIndependentProgID** — funkcja (wstawiane przez **coclass** atrybut).  
  
## <a name="example"></a>Przykład  
 Zobacz [coclass](../windows/coclass.md) przykład użycie próbki **vi_progid —**.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**,`struct`|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Element TypeDef, Enum, Unii i struct — atrybuty](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
 [Klucz identyfikatora progID](http://msdn.microsoft.com/library/windows/desktop/dd542719)   
