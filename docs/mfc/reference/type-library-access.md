---
title: Dostęp do biblioteki typów
ms.date: 11/04/2016
helpviewer_keywords:
- type libraries [MFC], accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
ms.openlocfilehash: 23d4675bd3638d2effd1b967f0729f9e70dac6de
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420751"
---
# <a name="type-library-access"></a>Dostęp do biblioteki typów

Biblioteki typów uwidaczniają interfejsy kontrolki OLE innym aplikacjom obsługującym technologię OLE. Każdy formant OLE musi mieć bibliotekę typów, jeśli jeden lub więcej interfejsów ma być narażony.

Następujące makra pozwalają formantowi OLE zapewnić dostęp do własnej biblioteki typów:

### <a name="type-library-access"></a>Dostęp do biblioteki typów

|||
|-|-|
|[DECLARE_OLETYPELIB](#declare_oletypelib)|Deklaruje `GetTypeLib` funkcję członkowską kontrolki OLE (należy ją użyć w deklaracji klasy).|
|[IMPLEMENT_OLETYPELIB](#implement_oletypelib)|Implementuje funkcję członkowską `GetTypeLib` formantu OLE (musi być używana w implementacji klasy).|

##  <a name="declare_oletypelib"></a>DECLARE_OLETYPELIB

Deklaruje funkcję członkowską `GetTypeLib` klasy kontrolki.

```
DECLARE_OLETYPELIB(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy kontrolki powiązanej z biblioteką typów.

### <a name="remarks"></a>Uwagi

Użyj tego makra w pliku nagłówkowym klasy kontrolki.

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDISP. h

##  <a name="implement_oletypelib"></a>IMPLEMENT_OLETYPELIB

Implementuje funkcję członkowską `GetTypeLib` formantu.

```
IMPLEMENT_OLETYPELIB(class_name, tlid, wVerMajor,  wVerMinor)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy kontrolki powiązanej z biblioteką typów.

*tlid*<br/>
Numer IDENTYFIKACYJNy biblioteki typów.

*wVerMajor*<br/>
Główny numer wersji biblioteki typów.

*wVerMinor*<br/>
Numer wersji pomocniczej biblioteki typów.

### <a name="remarks"></a>Uwagi

To makro musi pojawić się w pliku implementacji dla każdej klasy kontrolki, która używa makra DECLARE_OLETYPELIB.

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDISP. h

## <a name="see-also"></a>Zobacz też

[Makra i Globals](../../mfc/reference/mfc-macros-and-globals.md)
