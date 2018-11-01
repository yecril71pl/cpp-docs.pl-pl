---
title: DHtmlUrlEventMapEntry — Struktura
ms.date: 11/04/2016
f1_keywords:
- DHtmlUrlEventMapEntry
helpviewer_keywords:
- DHtmlUrlEventMapEntry structure [MFC]
ms.assetid: 43117c1f-1a51-406c-aa2f-fea647080049
ms.openlocfilehash: 0a1dc86080c094a7ac89940cd43a8edac973e10c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50431632"
---
# <a name="dhtmlurleventmapentry-structure"></a>DHtmlUrlEventMapEntry — Struktura

`DHtmlUrlEventMapEntry` Struktury obsługuje wielu adresów URL zdarzeń mapy.

## <a name="syntax"></a>Składnia

```
struct DHtmlUrlEventMapEntry
{
LPCTSTR szUrl;
const DHtmlEventMapEntry *pEventMap;
};
```

#### <a name="parameters"></a>Parametry

*szUrl*<br/>
Adres URL.

*pEventMap*<br/>
Mapa zdarzeń skojarzone z adresem URL.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdhtml.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

