---
title: ProgID | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.progid
dev_langs:
- C++
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f2b2d2168b568c74c5404cc83bab1e5f77570773
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="progid"></a>progid
Określa identyfikator ProgID dla obiekt COM.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ progid(  
   name  
) ];  
```  
  
#### <a name="parameters"></a>Parametry  
 *Nazwa*  
 Identyfikator ProgID reprezentujący obiekt.  
  
 ProgID stanowi wersję identyfikator klasy (CLSID) używany do identyfikowania obiektów COM/ActiveX zrozumiałą dla użytkownika.  
  
## <a name="remarks"></a>Uwagi  
 **Progid** atrybutu C++ pozwala określić identyfikator ProgID dla obiekt COM. Identyfikator ProgID ma formę *name1.name2.version*. Jeśli nie określisz *wersji* dla identyfikatora ProgID wersja domyślna to 1. Jeśli nie określisz *name1.name2*, nazwa domyślna to *classname.classname*. Jeśli nie określisz **progid** i określ **vi_progid —**, *name1.name2* są pobierane z **vi_progid —** i (dalej sekwencyjne Liczba) wersja jest dołączany.  
  
 Jeśli blok atrybutu, który używa **progid** również nie używa `uuid`, kompilator będzie sprawdzać rejestru, aby sprawdzić, czy `uuid` istnieje dla określonego **progid**. Jeśli **progid** nie zostanie określony, wersja (i nazwa klasy coclass, w przypadku tworzenia klasy coclass) będą używane do generowania **progid**.  
  
 **ProgID** oznacza **coclass** atrybutu, oznacza to, że jeśli określisz **progid**, jest odpowiednikiem określenie **coclass** i  **ProgID** atrybutów.  
  
 **Progid** atrybutu powoduje, że klasa automatycznie rejestrowana o określonej nazwie. Nie zawiera pliku .idl wygenerowanego **progid** wartość.  
  
 Jeśli ten atrybut jest używany w projekcie, który używa ATL, zachowanie zmiany atrybutów. Oprócz powyższych zachowanie podanych informacji o tym atrybutem jest używany w **GetProgID** funkcja wstrzyknięte przez **coclass** atrybutu. Aby uzyskać więcej informacji, zobacz [coclass](../windows/coclass.md) atrybutu.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [coclass](../windows/coclass.md) użytku próbki **progid**.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**, `struct`|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|Brak|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty IDL](../windows/idl-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
 [Element TypeDef, Enum, Unii i struct — atrybuty](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Klucz identyfikatora progID](http://msdn.microsoft.com/library/windows/desktop/dd542719)   
