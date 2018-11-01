---
title: Struktura COMPAREITEMSTRUCT
ms.date: 11/04/2016
f1_keywords:
- COMPAREITEMSTRUCT
helpviewer_keywords:
- COMPAREITEMSTRUCT structure [MFC]
ms.assetid: 4b7131a5-5c7d-4e98-aac7-e85650262b52
ms.openlocfilehash: 78a6e76ee3bbac5b32eb4bccf45578e63f763b75
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465419"
---
# <a name="compareitemstruct-structure"></a>Struktura COMPAREITEMSTRUCT

`COMPAREITEMSTRUCT` Struktury dostarcza identyfikatorów i dostarczony aplikacji danych dla dwóch elementów w polu listy posortowany, rysowanych przez właściciela lub pola kombi.

## <a name="syntax"></a>Składnia

```
typedef struct tagCOMPAREITEMSTRUCT {
    UINT CtlType;
    UINT CtlID;
    HWND hwndItem;
    UINT itemID1;
    DWORD itemData1;
    UINT itemID2;
    DWORD itemData2;
} COMPAREITEMSTRUCT;
```

#### <a name="parameters"></a>Parametry

*CtlType*<br/>
ODT_LISTBOX (który określa pole listy rysowane przez właściciela) lub ODT_COMBOBOX (który określa pola kombi rysowanego przez właściciela).

*CtlID*<br/>
Identyfikator formantu dla pola listy lub pola kombi.

*hwndItem*<br/>
Uchwyt okna kontrolki.

*itemID1*<br/>
Indeks pierwszego elementu w polu listy lub pola kombi, którą jest porównywany.

*itemData1*<br/>
Dane dostarczone przez aplikację dla pierwszego elementu, którą jest porównywany. Ta wartość została przekazana wywołanie, które dodano element do pola kombi lub listy.

*itemID2*<br/>
Indeks drugiego elementu w polu listy lub pola kombi, którą jest porównywany.

*itemData2*<br/>
Dane dostarczone przez aplikację drugiego elementu, którą jest porównywany. Ta wartość została przekazana wywołanie, które dodano element do pola kombi lub listy.

## <a name="remarks"></a>Uwagi

Zawsze, gdy aplikacja dodaje nowy element, aby pole listy rysowane przez właściciela lub pola kombi utworzone przy użyciu stylu CBS_SORT lub LBS_SORT, Windows wysyła właściciela WM_COMPAREITEM komunikat. *LParam* parametr wiadomości zawiera długie wskaźnik do `COMPAREITEMSTRUCT` struktury. Po odebraniu wiadomości, właściciel porównuje dwa elementy i zwraca wartość wskazującą, który element sortowane przed innymi.

## <a name="requirements"></a>Wymagania

**Nagłówek:** winuser.h

## <a name="see-also"></a>Zobacz też

[Struktury, style, wywołania zwrotne i mapy komunikatów](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem)

