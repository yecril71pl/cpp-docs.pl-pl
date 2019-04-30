---
title: RDX (atrybut COM C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.rdx
helpviewer_keywords:
- rdx attribute
ms.assetid: ff8e4312-c1ad-4934-bdaa-86f54409651e
ms.openlocfilehash: 2790c3de01d21242daee73fc442ad22d88739355
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407500"
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

## <a name="see-also"></a>Zobacz także

[Atrybuty COM](com-attributes.md)<br/>
[registration_script](registration-script.md)