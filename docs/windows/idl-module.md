---
title: idl_module | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.idl_module
dev_langs:
- C++
helpviewer_keywords:
- idl_module attribute
ms.assetid: 3578b337-e38a-4334-b747-15404c02dbc0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 11547a3fb1bd46a1e2edb8ce9dd0a6547464f796
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882527"
---
# <a name="idlmodule"></a>idl_module
Określa punkt wejścia w pliku dll.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ idl_module (   
   name=module_name,   
   dllname=dll,   
   uuid="uuid",   
   helpstring="help text",   
   helpstringcontext=helpcontextID,   
   helpcontext=helpcontext,   
   hidden,   
   restricted  
) ]  
function declaration  
```  
  
#### <a name="parameters"></a>Parametry  
 **Nazwa**  
 Zdefiniowane przez użytkownika nazwę tego bloku kodu, który będzie widoczny w pliku .idl.  
  
 **DllName** (opcjonalnie)  
 Plik .dll, który zawiera eksportu.  
  
 `uuid` (opcjonalnie)  
 Unikatowy identyfikator.  
  
 **HelpString —** (opcjonalnie)  
 Ciąg znaków używany do opisywania biblioteki typów.  
  
 **helpstringcontext —** (opcjonalnie)  
 Identyfikator tematu pomocy w formacie pliku .hlp lub .chm.  
  
 **helpcontext** (opcjonalnie)  
 Identyfikator pomocy dla tego typu biblioteki.  
  
 **ukryte** (opcjonalnie)  
 Parametr, który zapobiega wyświetlaniu biblioteki. Zobacz [ukryte](http://msdn.microsoft.com/library/windows/desktop/aa366861) atrybutu MIDL, aby uzyskać więcej informacji.  
  
 ***ograniczone*** (opcjonalnie)  
 Elementy członkowskie biblioteki nie można wywołać arbitralnie. Zobacz [ograniczeniami](http://msdn.microsoft.com/library/windows/desktop/aa367157) atrybutu MIDL, aby uzyskać więcej informacji.  
  
 *deklaracji funkcji*  
 Funkcja, który będzie definiował.  
  
## <a name="remarks"></a>Uwagi  
 `idl_module` Atrybut C++ pozwala określić punkt wejścia w pliku dll, dzięki czemu można zaimportować z pliku dll.  
  
 **Idl_module** atrybut ma podobne do funkcji [modułu](http://msdn.microsoft.com/library/windows/desktop/aa367099) MIDL atrybutu.  
  
 Możesz wyeksportować niczego z obiektu COM, który można eksportować z pliku .dll umieszczenie punktu wejścia biblioteki DLL w bloku biblioteki pliku .idl.  
  
 Sieci należy użyć `idl_module` w dwóch krokach. Najpierw należy zdefiniować pary nazwa/DLL. Następnie, jeśli używasz `idl_module` do określenia punktu wejścia, określ nazwę oraz wszelkie dodatkowe atrybuty.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób użycia `idl_module` atrybutu:  
  
```  
// cpp_attr_ref_idl_module.cpp  
// compile with: /LD  
[idl_quote("midl_pragma warning(disable:2461)")];  
[module(name="MyLibrary"), idl_module(name="MyLib", dllname="xxx.dll")];  
[idl_module(name="MyLib"), entry(4), usesgetlasterror]  
void FuncName(int i);  
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
 [entry](../windows/entry.md)   
