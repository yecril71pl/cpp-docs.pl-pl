---
title: Struktura DEVNAMES | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DEVNAMES
dev_langs:
- C++
helpviewer_keywords:
- DEVNAMES [MFC]
ms.assetid: aac97f60-2169-471a-ba5d-c0baed9eed9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 637843873bbb0e12a76168bd08b613e14b391ef8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392466"
---
# <a name="devnames-structure"></a>Struktura DEVNAMES

`DEVNAMES` Struktura zawiera ciągi, które identyfikują sterownika, urządzenia i nazwy portu wyjściowego dla drukarki.

## <a name="syntax"></a>Składnia

```
typedef struct tagDEVNAMES { /* dvnm */
    WORD wDriverOffset;
    WORD wDeviceOffset;
    WORD wOutputOffset;
    WORD wDefault; */* driver,
    device,
    and port-name strings follow wDefault */
} DEVNAMES;
```

#### <a name="parameters"></a>Parametry

*wDriverOffset*<br/>
(Wejście/wyjście) Określa przesunięcie w znakach na ciąg zakończony wartością null zawierający nazwę pliku (bez rozszerzenia) sterownika urządzenia. W danych wejściowych ten ciąg jest używany do określenia drukarki na początku wyświetlić w oknie dialogowym.

*wDeviceOffset*<br/>
(Wejście/wyjście) Określa przesunięcie w znakach na ciąg zakończony znakiem null (maksymalnie 32 bajty, w tym o wartości null) zawierający nazwę urządzenia. Ten ciąg musi być taka sama jak `dmDeviceName` członkiem [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) struktury.

*wOutputOffset*<br/>
(Wejście/wyjście) Określa przesunięcie w znakach ciąg zakończony znakiem null, która zawiera nazwy urządzenia systemu DOS dla średnich wyjściowego fizycznej (port wyjściowy).

*wDefault*<br/>
Określa, czy ciągi są zawarte w `DEVNAMES` struktury zidentyfikować zostanie użyta drukarka domyślna. Ten ciąg jest używany, aby zweryfikować, że zostanie użyta drukarka domyślna nie została zmieniona od czasu ostatniej operacji drukowania. W danych wejściowych, jeśli jest ustawiona flaga DN_DEFAULTPRN, innych wartości w `DEVNAMES` struktury są porównywane z bieżącej domyślnej drukarki. Jeśli dowolne ciągi nie są zgodne, zostanie wyświetlony komunikat ostrzegawczy, informujący użytkownika, że dokument może być konieczne sformatowany. W danych wyjściowych `wDefault` element członkowski zostanie zmieniony tylko wtedy, gdy zostało wyświetlone okno dialogowe Ustawienia wydruku i użytkownik wybrał przycisk OK. Flaga DN_DEFAULTPRN jest ustawiona, jeśli wybrano zostanie użyta drukarka domyślna. Jeśli wybrano drukarkę, flaga nie jest ustawiona. Wszystkie bity w tym elemencie członkowskim są zarezerwowane do użytku wewnętrznego przez tę procedurę, okno dialogowe drukowania.

## <a name="remarks"></a>Uwagi

`PrintDlg` Funkcja używa tych ciągów do zainicjowania elementów członkowskich w oknie dialogowym drukowania zdefiniowaną przez system. Gdy użytkownik zamyka okno dialogowe, informacje na temat wybrane drukarki jest zwracany w tej struktury.

## <a name="requirements"></a>Wymagania

**Nagłówek:** commdlg.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CPrintDialog::CreatePrinterDC](../../mfc/reference/cprintdialog-class.md#createprinterdc)


