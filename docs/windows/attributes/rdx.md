---
title: RDX (atrybut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.rdx
helpviewer_keywords:
- rdx attribute
ms.assetid: ff8e4312-c1ad-4934-bdaa-86f54409651e
ms.openlocfilehash: f61eaf535102c8885e828176434acf221dfe2457
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836884"
---
# <a name="rdx"></a>rdx

Tworzy klucz rejestru lub modyfikuje istniejący klucz rejestru.

## <a name="syntax"></a>Składnia

```cpp
[ rdx(key, valuename=NULL, regtype) ]
```

### <a name="parameters"></a>Parametry

*głównych*<br/>
Nazwa klucza, który ma zostać utworzony lub otwarty.

*Pełna*<br/>
Obowiązkowe Określa pole wartości, które ma zostać ustawione. Jeśli pole wartości o tej nazwie nie istnieje jeszcze w kluczu, zostanie dodane.

*regtype*<br/>
Typ klucza rejestru, który jest dodawany. Może być jedną z następujących wartości: `text` , `dword` , `binary` , lub `CString` .

## <a name="remarks"></a>Uwagi

Atrybut **RDX** C++ tworzy lub modyfikuje istniejący klucz rejestru dla składnika com. Ten atrybut dodaje makro BEGIN_RDX_MAP do obiektu, który implementuje docelowy element członkowski. `RegistryDataExchange`, funkcja wstrzykiwana jako wynik makra BEGIN_RDX_MAP, może służyć do transferowania danych między Rejestrem a elementami członkowskimi danych

Ten atrybut może być używany w połączeniu z atrybutami [coclass](coclass.md), [ProgID](progid.md)lub [vi_progid](vi-progid.md) lub innymi atrybutami, które implikują jeden z nich.

## <a name="requirements"></a>Wymagania

| Kontekst atrybutu | Wartość |
|-|-|
|**Dotyczy**|**`class`** lub **`struct`** członek|
|**Powtarzalne**|Nie|
|**Wymagane atrybuty**|Brak|
|**Nieprawidłowe atrybuty**|Brak|

Aby uzyskać więcej informacji na temat kontekstów atrybutów, zobacz [konteksty atrybutów](cpp-attributes-com-net.md#contexts).

## <a name="example"></a>Przykład

Poniższy kod dodaje klucz rejestru o nazwie CMyClass do systemu opisującego składnik COM.

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
