---
title: Dostęp do biblioteki typów
ms.date: 11/04/2016
helpviewer_keywords:
- type libraries [MFC], accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
ms.openlocfilehash: 1794e16489ab48d919bbd4116588fba4b74b88d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372872"
---
# <a name="type-library-access"></a>Dostęp do biblioteki typów

Biblioteki typów udostępniają interfejsy formantu OLE innym aplikacjom obsługującym ole. Każdy formant OLE musi mieć bibliotekę typów, jeśli jeden lub więcej interfejsów mają być widoczne.

Następujące makra umożliwiają formancie OLE zapewnienie dostępu do własnej biblioteki typów:

### <a name="type-library-access"></a>Dostęp do biblioteki typów

|||
|-|-|
|[DECLARE_OLETYPELIB](#declare_oletypelib)|Deklaruje funkcję `GetTypeLib` elementu członkowskiego formantu OLE (musi być używany w deklaracji klasy).|
|[IMPLEMENT_OLETYPELIB](#implement_oletypelib)|Implementuje `GetTypeLib` funkcję elementu członkowskiego formantu OLE (musi być używany w implementacji klasy).|

## <a name="declare_oletypelib"></a><a name="declare_oletypelib"></a>DECLARE_OLETYPELIB

Deklaruje funkcję `GetTypeLib` elementu członkowskiego klasy kontrolnej.

```
DECLARE_OLETYPELIB(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy formantu związane z biblioteką typów.

### <a name="remarks"></a>Uwagi

Użyj tego makra w pliku nagłówka klasy kontrolnej.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="implement_oletypelib"></a><a name="implement_oletypelib"></a>IMPLEMENT_OLETYPELIB

Implementuje funkcję `GetTypeLib` elementu członkowskiego formantu.

```
IMPLEMENT_OLETYPELIB(class_name, tlid, wVerMajor,  wVerMinor)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy formantu związane z biblioteką typów.

*tlid ( tlid )*<br/>
Numer identyfikatora biblioteki typów.

*wVerMajor*<br/>
Numer głównej wersji biblioteki typów.

*wVerMinor*<br/>
Numer wersji pomocniczej biblioteki typów.

### <a name="remarks"></a>Uwagi

To makro musi pojawić się w pliku implementacji dla każdej klasy formantu, która używa makra DECLARE_OLETYPELIB.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="see-also"></a>Zobacz też

[Makra i globals](../../mfc/reference/mfc-macros-and-globals.md)
