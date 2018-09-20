---
title: Struktura PAINTSTRUCT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- PAINTSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- PAINTSTRUCT structure [MFC]
ms.assetid: 81ce4993-3e89-43b2-8c98-7946f1314d24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 531dbc3c0e9b609aeaf5d9179491aa0fb3990363
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382924"
---
# <a name="paintstruct-structure"></a>Struktura PAINTSTRUCT

`PAINTSTRUCT` Struktura zawiera informacje, który może służyć do malowania obszaru klienckiego okna.

## <a name="syntax"></a>Składnia

```
typedef struct tagPAINTSTRUCT {
    HDC hdc;
    BOOL fErase;
    RECT rcPaint;
    BOOL fRestore;
    BOOL fIncUpdate;
    BYTE rgbReserved[16];
} PAINTSTRUCT;
```

#### <a name="parameters"></a>Parametry

*elementu hdc*<br/>
Identyfikuje kontekst wyświetlania ma być używany do malowania.

*fErase*<br/>
Określa, czy tło powinien być narysowany ponownie. Nie jest równa 0, jeśli aplikacja ponownie narysować tła. Aplikacja jest odpowiedzialna za rysowania tła, jeśli klasę okna Windows została utworzona bez pędzel tła (zobacz opis `hbrBackground` członkiem [WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576) struktury w zestawie Windows SDK).

*rcPaint*<br/>
Określa lewym górnym i dolnym prawym rogu prostokąta, w której zażądano malowania.

*fRestore*<br/>
Zastrzeżoną składową. Jest ono używane wewnętrznie przez Windows.

*fIncUpdate*<br/>
Zastrzeżoną składową. Jest ono używane wewnętrznie przez Windows.

*rgbReserved [16]*<br/>
Zastrzeżoną składową. Zastrzeżone blok pamięć używana wewnętrznie przez Windows.

## <a name="requirements"></a>Wymagania

**Nagłówek:** winuser.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CPaintDC::m_ps](../../mfc/reference/cpaintdc-class.md#m_ps)

