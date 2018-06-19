---
title: Importuj | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.import
dev_langs:
- C++
helpviewer_keywords:
- import attribute
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b371cd1094a49f8a629cb6f8e880fd1210670f91
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877270"
---
# <a name="import"></a>import
Określa innego pliku .idl, .odl — lub nagłówek zawierający definicje, które chcesz odwołać się z sieci głównego IDL.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ import(  
   idl_file  
) ];  
```  
  
#### <a name="parameters"></a>Parametry  
 `idl_file`  
 Nazwa pliku .idl, który ma zostać zaimportowany do biblioteki typu bieżącego projektu.  
  
## <a name="remarks"></a>Uwagi  
 **Zaimportować** atrybut C++ powoduje `#import` instrukcji do umieszczenia poniżej `import "docobj.idl"` instrukcji w pliku .idl wygenerowany. **Zaimportować** atrybut ma te same funkcje co [zaimportować](http://msdn.microsoft.com/library/windows/desktop/aa367047) MIDL atrybutu.  
  
 **Zaimportować** atrybutu tylko umieszcza określonego pliku w pliku .idl, który zostanie wygenerowany przez projekt; **zaimportować** atrybutu nie zezwala na wywołania konstrukcje w określonym pliku z kodu źródłowego w projekcie.  Aby wywołać konstrukcje w określonym pliku z kodu źródłowego w projekcie, albo użyć [#import](../preprocessor/hash-import-directive-cpp.md) i `embedded_idl` atrybutu lub użytkownik może zawierać plik .h dla `idl_file`, jeśli istnieje plik .h.  
  
## <a name="example"></a>Przykład  
 Następujący kod:  
  
```  
// cpp_attr_ref_import.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[import(import.idl)];  
```  
  
 Tworzy następujący kod w pliku .idl wygenerowanego:  
  
```  
import "docobj.idl";  
import "import.idl";  
  
[ uuid(EED3644C-8488-3ECD-BA97-147DB3CDB499), version(1.0) ]  
library MyLib {  
   importlib("stdole2.tlb");  
   importlib("olepro32.dll");  
...  
```  
  
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
 [importidl —](../windows/importidl.md)   
 [importlib](../windows/importlib.md)   
 [Obejmują](../windows/include-cpp.md)   
 [includelib —](../windows/includelib-cpp.md)   
