---
title: idl_module | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.idl_module
dev_langs:
- C++
helpviewer_keywords:
- idl_module attribute
ms.assetid: 3578b337-e38a-4334-b747-15404c02dbc0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f052692686149b247a50c0d89e77797f4f48fab3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
  
 `uuid`(opcjonalnie)  
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
