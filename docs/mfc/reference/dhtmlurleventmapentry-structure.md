---
title: DHtmlUrlEventMapEntry — Struktura
ms.date: 11/04/2016
f1_keywords:
- DHtmlUrlEventMapEntry
helpviewer_keywords:
- DHtmlUrlEventMapEntry structure [MFC]
ms.assetid: 43117c1f-1a51-406c-aa2f-fea647080049
ms.openlocfilehash: c9b58067a9c8b6a71cd22b654a2f82ba0f8bfe36
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292656"
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

## <a name="see-also"></a>Zobacz także

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)
