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
ms.openlocfilehash: cbcbce1e476fef0d076f9c25b46b3166c1eb5935
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624351"
---
# <a name="message-handling-and-command-targets"></a>Obsługa komunikatów i obiekty docelowe poleceń

Interfejs wysyłania poleceń `IOleCommandTarget` definiuje prosty i rozszerzalny mechanizm wykonywania zapytań i wykonywania poleceń. Ten mechanizm jest łatwiejszy niż Automatyzacja `IDispatch` , ponieważ opiera się wyłącznie na standardowym zestawie poleceń; polecenia rzadko mają argumenty i nie są związane z żadnymi informacjami o typie (zabezpieczenia typu są również zmniejszane dla argumentów polecenia).

W projekcie interfejsu wysyłania poleceń każde polecenie należy do "grupy poleceń", która jest sama identyfikowana przy użyciu **identyfikatora GUID**. W związku z tym każdy może definiować nową grupę i definiować wszystkie polecenia w tej grupie bez konieczności koordynowania z firmą Microsoft ani innego dostawcy. (Zasadniczo jest to ten sam sposób definiowania jako **dispinterface** i **identyfikatory SPID** w automatyzacji. Ta funkcja jest nakładana na siebie, chociaż mechanizm routingu poleceń jest przeznaczony tylko dla routingu poleceń, a nie do obsługi skryptów/programowania na dużą skalę jako uchwytów automatyzacji.

`IOleCommandTarget`obsługuje następujące scenariusze:

- Gdy obiekt jest aktywowany w miejscu, zazwyczaj wyświetlane są tylko paski narzędzi obiektu, a paski narzędzi obiektu mogą mieć przyciski dla niektórych poleceń kontenera, takich jak **Drukowanie**, **Podgląd wydruku**, **Zapisywanie**, **nowe**, **powiększanie**i inne. (W przypadku standardów aktywacji w miejscu zaleca się, aby obiekty usuwają takie przyciski z pasków narzędzi lub co najmniej je wyłączyć. Ten projekt umożliwia włączenie tych poleceń, a następnie przekierowanie do odpowiedniej procedury obsługi. Obecnie nie istnieje mechanizm, dla którego obiekt wysyła te polecenia do kontenera.

- Gdy aktywny dokument jest osadzony w kontenerze aktywnego dokumentu (na przykład Office Binder), może być konieczne wysłanie przez kontener poleceń takich jak **Drukowanie**, **Konfiguracja strony**, **Właściwości**i inne do zawartego aktywnego dokumentu.

To proste rozsyłanie poleceń może być obsługiwane za poorednictwem istniejących standardów automatyzacji i `IDispatch` . Jednak narzuty związane z programem `IDispatch` są w tym miejscu większe niż jest to konieczne, dlatego `IOleCommandTarget` zapewnia prostsze środki do osiągnięcia tego samego końca:

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

W `QueryStatus` tym miejscu Metoda sprawdza, czy określony zestaw poleceń, zestaw identyfikowany za pomocą **identyfikatora GUID**, jest obsługiwany. To wywołanie wypełnia tablicę wartości **OLECMD** (struktury) z obsługiwaną listą poleceń, a także zwraca tekst opisujący nazwę polecenia i/lub informacje o stanie. Gdy obiekt wywołujący chce wywołać polecenie, może przekazać polecenie (i **Identyfikator GUID**zestawu) do programu `Exec` wraz z opcjami i argumentami, zwracając wartość zwracaną.

## <a name="see-also"></a>Zobacz też

[Kontenery dokumentów aktywnych](active-document-containers.md)
