---
title: Obsługa komunikatów i obiekty docelowe poleceń
ms.date: 11/04/2016
f1_keywords:
- IOleCommandTarget
helpviewer_keywords:
- command targets [MFC]
- message handling [MFC], active documents
- IOleCommandTarget interface [MFC]
- command routing [MFC], command targets
ms.assetid: e45ce14c-e6b6-4262-8f3b-4e891e0ec2a3
ms.openlocfilehash: 702cb96da13d6109c17a28e58c08a30af3f77fd4
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302744"
---
# <a name="message-handling-and-command-targets"></a>Obsługa komunikatów i obiekty docelowe poleceń

Interfejs ekspedycji polecenia `IOleCommandTarget` definiuje prosty i rozszerzalny mechanizm zapytań i wykonywania poleceń. Ten mechanizm jest prostsze niż usługi Automation `IDispatch` ponieważ opiera się wyłącznie na zestaw standardowych poleceń; polecenia rzadko mają argumentów i uczestniczy nie informacji o typie (bezpieczeństwo typów będzie mniejsza także argumentów polecenia).

W projekcie interfejsu wysyłania polecenia, każdego polecenia należy do "grupy poleceń", która jest sam identyfikowany za pomocą **GUID**. W związku z tym każdy może zdefiniować nowe grupy i definiowania wszystkich poleceń w tej grupie bez konieczności koordynowania z firmą Microsoft lub innych dostawców. (To jest zasadniczo ten sam sposób definicji jako **dispinterface** oraz **DISPID** w usłudze Automation. Jest nakładają się w tym miejscu, mimo że ten mechanizm routingu poleceń jest tylko w przypadku routingu poleceń, a nie dla skryptów/programowania na dużą skalę jako usługi Automation obsługuje).

`IOleCommandTarget` obsługuje następujące scenariusze:

- Gdy obiekt jest aktywowany tylko paski narzędzi obiektu zwykle są wyświetlane i paski narzędzi obiektu może być przycisków dla niektórych poleceń kontenera, takich jak w miejscu **drukowania**, **Podgląd wydruku**,  **Zapisz**, **New**, **powiększenia**i innym osobom. (Aktywacji w miejscu, zalecane standardy, Usuń obiekty takie przyciski ich paski narzędzi, albo w co najmniej je wyłączyć. Ten projekt umożliwia tych poleceń, należy włączyć i jeszcze kierowane do obsługi prawo). Obecnie nie ma mechanizmu dla obiektu do wysyłania poleceń do kontenera.

- Osadzone aktywnego dokumentu w kontenerze dokumentów aktywnych (np. Office Binder) kontener może być konieczne wysyłanie poleceń takich **drukowania**, **ustawienia strony**, **właściwości**i inne osoby do zamkniętego aktywnego dokumentu.

Marszruty prostego polecenia, można obsługiwane przez istniejące standardy automatyzacji i `IDispatch`. Jednak obciążenie związane z `IDispatch` jest większa niż jest to konieczne, dzięki czemu `IOleCommandTarget` zapewnia prostszy sposób osiągnięcia tego samego kończy się:

```
interface IOleCommandTarget : IUnknown
    {
    HRESULT QueryStatus(
        [in] GUID *pguidCmdGroup,
        [in] ULONG cCmds,
        [in,out][size_is(cCmds)] OLECMD *prgCmds,
        [in,out] OLECMDTEXT *pCmdText);
    HRESULT Exec(
        [in] GUID *pguidCmdGroup,
        [in] DWORD nCmdID,
        [in] DWORD nCmdExecOpt,
        [in] VARIANTARG *pvaIn,
        [in,out] VARIANTARG *pvaOut);
    }
```

`QueryStatus` Tutaj metoda sprawdza, czy określony zestaw poleceń, zestaw jest identyfikowany za pomocą **GUID**, jest obsługiwane. To wywołanie wypełnia tablicę **OLECMD** (struktury) wartościami listę obsługiwanych poleceń, a także zwraca tekst opisu nazwę informacji polecenia i/lub stanu. Gdy obiekt wywołujący chce Wywołaj polecenie, można go przekazać polecenie (i zestawu **GUID**) do `Exec` oraz opcje i argumenty powrót do wartości zwracanej.

## <a name="see-also"></a>Zobacz także

[Kontenery dokumentów aktywnych](../mfc/active-document-containers.md)
