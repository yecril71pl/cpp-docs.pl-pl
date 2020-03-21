---
title: Błąd czasu wykonania języka C R6025
ms.date: 11/04/2016
f1_keywords:
- R6025
helpviewer_keywords:
- R6025
ms.assetid: afa06d98-9c36-445b-b3e7-b6409bc8e779
ms.openlocfilehash: d5edb08278b7b6b9b3eb62e92fc04410f96a8f09
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075126"
---
# <a name="c-runtime-error-r6025"></a>Błąd czasu wykonania języka C R6025

czyste wywołanie funkcji wirtualnej

> [!NOTE]
> Jeśli ten komunikat o błędzie wystąpi podczas uruchamiania aplikacji, aplikacja została zamknięta, ponieważ ma problem wewnętrzny. Najbardziej typową przyczyną tego błędu jest usterka w aplikacji lub uszkodzenie instalacji.
>
> Możesz wypróbować następujące kroki, aby naprawić ten błąd:
>
> - Użyj strony **aplikacje i funkcje** lub **programy i funkcje** w **Panelu sterowania** , aby naprawić lub ponownie zainstalować program.
> - Sprawdź, **Windows Update** w **Panelu sterowania** aktualizacje oprogramowania.
> - Sprawdź dostępność zaktualizowanej wersji aplikacji. Jeśli problem będzie nadal występował, skontaktuj się z dostawcą aplikacji.

**Informacje dla programistów**

Nie utworzono wystąpienia obiektu do obsługi czystego wywołania funkcji wirtualnej.

Ten błąd jest spowodowany wywoływaniem funkcji wirtualnej w abstrakcyjnej klasie podstawowej za pomocą wskaźnika, który jest tworzony przez rzutowanie do typu klasy pochodnej, ale w rzeczywistości jest wskaźnikiem do klasy bazowej. Może się to zdarzyć w przypadku rzutowania z typu **void** <strong>\*</strong> na wskaźnik do klasy, gdy element **void** <strong>\*</strong> został utworzony podczas konstruowania klasy bazowej.
