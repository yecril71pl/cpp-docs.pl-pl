---
title: RDX | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.rdx
dev_langs:
- C++
helpviewer_keywords:
- rdx attribute
ms.assetid: ff8e4312-c1ad-4934-bdaa-86f54409651e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 00ef28954a686dac72c8b7f55b86c88313e74643
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719723"
---
# <a name="rdx"></a>rdx

Tworzy klucz rejestru lub modyfikuje istniejący klucz rejestru.

## <a name="syntax"></a>Składnia

```cpp
[ rdx(
   key,
   valuename=NULL,
   regtype
) ]
```

### <a name="parameters"></a>Parametry

*Klucz*  
Nazwa klucza, który ma zostać utworzony lub otwarty.

*VALUENAME*  
(Opcjonalnie) Określa pole wartości do ustawienia. Jeśli wartość pola o tej nazwie już istnieje w kluczu, zostanie dodany.

*regtype*  
Typ klucza rejestru dodawane. Może być jedną z następujących czynności: `text`, `dword`, `binary`, lub `CString`.

## <a name="remarks"></a>Uwagi

**Rdx** atrybut C++ tworzy lub modyfikuje istniejący klucz rejestru dla składnika COM. Ten atrybut dodaje makro BEGIN_RDX_MAP do obiektu, który implementuje docelowy element członkowski. `RegistryDataExchange`, funkcja wprowadzonym w wyniku makro BEGIN_RDX_MAP może służyć do przesyłania danych między rejestru i elementy członkowskie danych

Ten atrybut może być używany w połączeniu z [coclass](../windows/coclass.md), [progid](../windows/progid.md), lub [vi_progid —](../windows/vi-progid.md) atrybuty lub innych oznacza jeden z nich.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa** lub **struktury** elementu członkowskiego|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](../windows/attribute-contexts.md).

## <a name="example"></a>Przykład

Poniższy kod dodaje klucza rejestru o nazwie MyValue systemowi opisujące składnika CMyClass COM.

```cpp
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
[registration_script](../windows/registration-script.md)  