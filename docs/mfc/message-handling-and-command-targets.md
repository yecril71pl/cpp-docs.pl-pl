---
title: Komunikat obsługi i obiekty docelowe poleceń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- IOleCommandTarget
dev_langs:
- C++
helpviewer_keywords:
- command targets [MFC]
- message handling [MFC], active documents
- IOleCommandTarget interface [MFC]
- command routing [MFC], command targets
ms.assetid: e45ce14c-e6b6-4262-8f3b-4e891e0ec2a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7184a6e8df67dfd220173c42bfa3e0580bd2cd3f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349470"
---
# <a name="message-handling-and-command-targets"></a>Obsługa komunikatów i obiekty docelowe poleceń
Interfejs wysyłania polecenia `IOleCommandTarget` definiuje proste i rozszerzalny mechanizm zapytań i wykonywania poleceń. Ten mechanizm jest łatwiejsze niż automatyzacja `IDispatch` ponieważ opiera się na standardowy zestaw poleceń; polecenia mają rzadko argumentów i uczestniczy nie informacji o typie (typ bezpieczeństwa będzie mniejsza dla argumentów polecenia również).  
  
 W projekcie interfejsu wysyłania polecenia, każde polecenie należy do "Grupa polecenia", którego jest się z **GUID**. W związku z tym każda osoba, która zdefiniować nowe grupy i zdefiniuj wszystkie polecenia w tej grupie bez konieczności koordynować z firmą Microsoft lub innego dostawcy. (To zasadniczo ten sam środek definicji jako **dispinterface** plus **identyfikator DISPID** w automatyzacji. Występuje nakładanie się w tym miejscu, chociaż ten mechanizm routingu poleceń jest tylko w przypadku routing poleceń, a nie dla skryptów/programowania na dużą skalę jako dojść do automatyzacji.)  
  
 `IOleCommandTarget` obsługuje następujące scenariusze:  
  
-   Gdy obiekt jest w miejscu aktywować, tylko zwykle są wyświetlane paski narzędzi obiektu i paski narzędzi obiektu może być przycisków dla niektórych poleceń kontenera, takich jak **drukowania**, **Podgląd wydruku**,  **Zapisz**, `New`, **powiększenie**i inne. (Aktywacja w miejscu, które zaleca standardy które obiekty Usuń tych przycisków z ich pasków narzędzi lub na najmniej je wyłączyć. Ten projekt umożliwia tych poleceń, należy włączyć i jeszcze kierowane do obsługi prawo). Obecnie nie istnieje mechanizm dla obiekt do wysyłania tych poleceń do kontenera.  
  
-   Podczas aktywnego dokumentu jest osadzony w kontenerze dokumentów aktywnych (np. Office Binder), kontener może być konieczne wysyłać polecenia takie **drukowania**, **ustawienia strony**, **właściwości**oraz innym osobom do zawartych w niej aktywnego dokumentu.  
  
 Marszruty prostego polecenia można obsługiwana przez istniejące standardy automatyzacji i `IDispatch`. Jednak obciążenie związane z `IDispatch` jest większa niż jest to konieczne, więc `IOleCommandTarget` zapewnia prostszy sposób osiągnięcia celów tej samej:  
  
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
  
 `QueryStatus` Tutaj metoda sprawdza, czy zestaw poleceń, zestaw oznaczone symbolem **GUID**, jest obsługiwana. To wywołanie wypełnia tablicę **OLECMD** wartości (struktury) z listy obsługiwanych poleceń, a także zwracanie tekst opisujący nazwa informacji polecenia i/lub stanu. Gdy obiekt wywołujący zamierza wywołania polecenia, można przekazać polecenie (wraz z zestawem **GUID**) do **Exec** oraz opcje i argumenty odzyskać wartości zwracanej.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontenery dokumentów aktywnych](../mfc/active-document-containers.md)

