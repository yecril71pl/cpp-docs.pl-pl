---
title: Identyfikator UUID (atrybuty C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.uuid
dev_langs:
- C++
helpviewer_keywords:
- uuid attribute
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e56793855b278e0631c39ebfcdc51669a001a24b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="uuid-c-attributes"></a>uuid (Atrybuty C++)
Określa unikatowy identyfikator dla klasy ani interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ uuid(  
   "uuid"  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *uuid*  
 128-bitowego, unikatowy identyfikator.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli nie określono definicji klasy lub interfejsu `uuid` atrybutu C++, a następnie kompilatora Visual C++ zapewni jeden. Po określeniu `uuid`, musi zawierać cudzysłowów.  
  
 Jeśli nie określisz `uuid`, a następnie kompilator wygeneruje tego samego identyfikatora GUID dla interfejsów lub klas o takiej samej nazwie w projektach inny atrybut na maszynie.  
  
 Uuidgen.exe lub Guidgen.exe służy do generowania własnych unikatowych identyfikatorów. (Aby Uruchom dowolne z tych narzędzi, kliknij przycisk **Start** i kliknij przycisk **Uruchom** w menu. Następnie wprowadź nazwę wymagane narzędzia.)  
  
 Gdy jest używany w projekcie, który nie używa również ATL, określając `uuid` atrybut jest taki sam jak określenie [uuid](../cpp/uuid-cpp.md) __declspec — modyfikator. Aby pobrać `uuid` klasy, można użyć [__uuidof](../cpp/uuidof-operator.md)  
  
## <a name="example"></a>Przykład  
 Zobacz [powiązania](../windows/bindable.md) przykład użycie próbki `uuid`.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**, `struct`, `interface`, **Unii**, `enum`|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty interfejsu](../windows/interface-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
 [Element TypeDef, Enum, Unii i struct — atrybuty](../windows/typedef-enum-union-and-struct-attributes.md)   
 [uuid](http://msdn.microsoft.com/library/windows/desktop/aa367302)   
