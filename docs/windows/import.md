---
title: Importowanie | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: f0b7498ce36243d2f7a7014b8fa9041a1a7378d2
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604710"
---
# <a name="import"></a>import
Określa innego pliku .idl, .odl — lub nagłówek zawierający definicje, który ma zostać utworzone odwołanie z sieci głównego pliku IDL.  
  
## <a name="syntax"></a>Składnia  
  
```  
[ import(  
   idl_file  
) ];  
```  
  
### <a name="parameters"></a>Parametry  
 *idl_file*  
 Nazwa pliku .idl, który ma zostać zaimportowany do biblioteki typów w bieżącym projekcie.  
  
## <a name="remarks"></a>Uwagi  
 **Zaimportować** atrybut C++ powoduje `#import` instrukcję, aby umieszczona pod `import "docobj.idl"` instrukcja w pliku .idl wygenerowany. **Zaimportować** atrybut ma taką samą funkcjonalność jak [zaimportować](http://msdn.microsoft.com/library/windows/desktop/aa367047) atrybutów w MIDL.  
  
 **Zaimportować** atrybutu tylko umieszcza określonego pliku w pliku .idl, który zostanie wygenerowany w projekcie; **zaimportować** atrybutu nie zezwala na wywołania konstrukcje w określonym pliku z kodem źródłowym w projekcie.  Aby wywołać konstrukcje w określonym pliku z kodem źródłowym w projekcie, albo użyć [#import](../preprocessor/hash-import-directive-cpp.md) i `embedded_idl` lub atrybut może znajdować się plik .h dla *idl_file*, jeśli istnieje plik .h klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy kod:  
  
```cpp  
// cpp_attr_ref_import.cpp  
// compile with: /LD  
[module(name="MyLib")];  
[import(import.idl)];  
```  
  
 generuje następujący kod w pliku .idl wygenerowanego:  
  
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
 [importidl —](../windows/importidl.md)   
 [importlib](../windows/importlib.md)   
 [Obejmują](../windows/include-cpp.md)   
 [includelib —](../windows/includelib-cpp.md)   