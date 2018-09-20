---
title: Dostęp do biblioteki typu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- type libraries [MFC], accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1a361c1e50945b19562082424c178a21191bd0b9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404744"
---
# <a name="type-library-access"></a>Dostęp do biblioteki typów

Biblioteki typów uwidacznia interfejsów, które kontrolki OLE do innych aplikacji obsługujących OLE. Każda kontrolka OLE musi mieć bibliotekę typów, jeśli co najmniej jeden interfejs narażonych.

Następujące makra Zezwalaj na kontrolkę OLE w celu zapewnienia dostępu do jego własnej biblioteki typów:

### <a name="type-library-access"></a>Dostęp do biblioteki typów

|||
|-|-|
|[DECLARE_OLETYPELIB](#declare_oletypelib)|Deklaruje `GetTypeLib` funkcji składowej typu kontrolkę OLE (muszą być używane w deklaracji klasy).|
|[IMPLEMENT_OLETYPELIB](#implement_oletypelib)|Implementuje `GetTypeLib` funkcji składowej typu kontrolkę OLE (muszą być używane w implementacji klasy).|

##  <a name="declare_oletypelib"></a>  DECLARE_OLETYPELIB

Deklaruje `GetTypeLib` funkcji składowej klasy kontrolki.

```
DECLARE_OLETYPELIB(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy kontrolki powiązane z biblioteki typów.

### <a name="remarks"></a>Uwagi

Użyj tego makra w pliku nagłówkowym klasy kontrolki.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

##  <a name="implement_oletypelib"></a>  IMPLEMENT_OLETYPELIB

Implementuje formant `GetTypeLib` funkcja elementu członkowskiego.

```
IMPLEMENT_OLETYPELIB(class_name, tlid, wVerMajor,  wVerMinor)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy kontrolki powiązane z biblioteki typów.

*tlid*<br/>
Numer identyfikacyjny biblioteki typów.

*wVerMajor*<br/>
Wpisz biblioteki główny numer wersji.

*wVerMinor*<br/>
Wpisz biblioteki pomocniczy numer wersji.

### <a name="remarks"></a>Uwagi

To makro musi znajdować się w pliku implementacji dla każdej klasy kontrolki, która używa DECLARE_OLETYPELIB — makro.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="see-also"></a>Zobacz też

[Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
