---
title: Dostęp do biblioteki typów
ms.date: 11/04/2016
helpviewer_keywords:
- type libraries [MFC], accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
ms.openlocfilehash: 55d6a56f566416bb25f3ee3ae508c86f17f0df99
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840456"
---
# <a name="type-library-access"></a>Dostęp do biblioteki typów

Biblioteki typów uwidaczniają interfejsy kontrolki OLE innym aplikacjom obsługującym technologię OLE. Każdy formant OLE musi mieć bibliotekę typów, jeśli jeden lub więcej interfejsów ma być narażony.

Następujące makra pozwalają formantowi OLE zapewnić dostęp do własnej biblioteki typów:

### <a name="type-library-access"></a>Dostęp do biblioteki typów

|Nazwa|Opis|
|-|-|
|[DECLARE_OLETYPELIB](#declare_oletypelib)|Deklaruje `GetTypeLib` funkcję członkowską formantu OLE (musi być użyta w deklaracji klasy).|
|[IMPLEMENT_OLETYPELIB](#implement_oletypelib)|Implementuje `GetTypeLib` funkcję członkowską formantu OLE (musi być używana w implementacji klasy).|

## <a name="declare_oletypelib"></a><a name="declare_oletypelib"></a> DECLARE_OLETYPELIB

Deklaruje `GetTypeLib` funkcję członkowską klasy kontrolki.

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

## <a name="implement_oletypelib"></a><a name="implement_oletypelib"></a> IMPLEMENT_OLETYPELIB

Implementuje `GetTypeLib` funkcję składową formantu.

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
