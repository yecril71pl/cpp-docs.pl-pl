---
title: wątkowość (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.threading
dev_langs:
- C++
helpviewer_keywords:
- threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f21ea8c16b4e09a5ad1845a10797be00f91b0d8f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="threading-c"></a>threading (C++)
Określa model wątkowości dla obiekt COM.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      [ threading(  
   model=enumeration  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 ***model*** (opcjonalnie)  
 Jeden z następujących model wątkowości:  
  
-   **apartamentu** (wątkowości typu apartment)  
  
-   **neutralne** (składników .NET Framework bez interfejsu użytkownika)  
  
-   **pojedynczy** (proste wątków)  
  
-   **bezpłatne** (bezpłatny wątków)  
  
-   **zarówno** (apartament, jak i wolnych wątków)  
  
 Wartość domyślna to **apartamentu**.  
  
## <a name="remarks"></a>Uwagi  
 **Wątkowość** C++ atrybut nie ma w pliku .idl wygenerowany, ale będzie używany w implementacji obiektu COM.  
  
 W projektach ATL Jeśli [coclass](../windows/coclass.md) również jest obecny, atrybut określony przez model wątkowości *modelu* jest przekazywana jako parametr szablonu w celu [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) — klasa , wstawiane przez **coclass** atrybutu.  
  
 **Wątkowość** atrybut chroni także dostęp do [event_source —](../windows/event-source.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [licencjonowane](../windows/licensed.md) przykład użycie próbki **wątkowość**.  
  
## <a name="requirements"></a>Wymagania  
  
### <a name="attribute-context"></a>Atrybut kontekstu  
  
|||  
|-|-|  
|**Dotyczy**|**Klasa**, `struct`|  
|**Powtarzalne**|Nie|  
|**Wymaganych atrybutów**|**coclass**|  
|**Nieprawidłowe atrybuty**|Brak|  
  
 Aby uzyskać więcej informacji na temat konteksty atrybutu, zobacz [konteksty atrybutu](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Atrybuty COM](../windows/com-attributes.md)   
 [Element TypeDef, Enum, Unii i struct — atrybuty](../windows/typedef-enum-union-and-struct-attributes.md)   
 [Atrybuty klasy](../windows/class-attributes.md)   
 [Obsługa wielowątkowości w przypadku starszego kodu (Visual C++)](../parallel/multithreading-support-for-older-code-visual-cpp.md)   
 [Neutralne Apartamentach](http://msdn.microsoft.com/library/windows/desktop/ms681813)   
