---
title: RDX (atrybut C++ COM) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/02/2018
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
ms.openlocfilehash: e48d71ace613eac040f83023f70f2a1f28d09f6e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50082311"
---
# <a name="rdx"></a>rdx

Tworzy klucz rejestru lub modyfikuje istniejący klucz rejestru.

## <a name="syntax"></a>Składnia

```cpp
[ rdx(key, valuename=NULL, regtype) ]
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Nazwa klucza, który ma zostać utworzony lub otwarty.

*VALUENAME*<br/>
(Opcjonalnie) Określa pole wartości do ustawienia. Jeśli wartość pola o tej nazwie już istnieje w kluczu, zostanie dodany.

*regtype*<br/>
Typ klucza rejestru dodawane. Może być jedną z następujących czynności: `text`, `dword`, `binary`, lub `CString`.

## <a name="remarks"></a>Uwagi

**Rdx** atrybut C++ tworzy lub modyfikuje istniejący klucz rejestru dla składnika COM. Ten atrybut dodaje makro BEGIN_RDX_MAP do obiektu, który implementuje docelowy element członkowski. `RegistryDataExchange`, funkcja wprowadzonym w wyniku makro BEGIN_RDX_MAP może służyć do przesyłania danych między rejestru i elementy członkowskie danych

Ten atrybut może być używany w połączeniu z [coclass](coclass.md), [progid](progid.md), lub [vi_progid —](vi-progid.md) atrybuty lub innych oznacza jeden z nich.

## <a name="requirements"></a>Wymagania

### <a name="attribute-context"></a>Kontekst atrybutu

|||
|-|-|
|**Dotyczy**|**Klasa** lub **struktury** elementu członkowskiego|
|**Powtarzalne**|Nie|
|**Wymaganych atrybutów**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat konteksty atrybutu zobacz [konteksty atrybutu](cpp-attributes-com-net.md#contexts).

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

[Atrybuty COM](com-attributes.md)<br/>
[registration_script](registration-script.md)