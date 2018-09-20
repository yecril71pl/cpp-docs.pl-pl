---
title: Przenieś lokalizację definicji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: c6d507ac-c61e-4da2-95c8-d504b42e2520
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5058e0b3bab1fb5fb5e8d52b55e3fa7c37fd8a4e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430064"
---
# <a name="move-definition-location"></a>Przenieś lokalizację definicji
**Co:** pozwala natychmiast przenoszenie definicji funkcji do odpowiedniego pliku nagłówka.

**Kiedy:** ma funkcję, która ma zostać przeniesiony do pliku nagłówka.

**Dlaczego:** można ręcznie przenieść tę funkcję, ale ta funkcja przeniesie go automatycznie, tworzenie pliku nagłówka, jeśli jest to wymagane.

**Jak:**

1. Umieść kursor tekstu lub myszy za pośrednictwem funkcji, dla którego chcesz przenieść.

   ![Wyróżniony kod](images/movedefinition_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Keyboard**
     * Naciśnij klawisz **Ctrl +.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Przenieś lokalizację definicji** z menu kontekstowego.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Przenieś lokalizację definicji** z menu kontekstowego.

1. Funkcja zostanie przeniesiony do odpowiedniego pliku nagłówka zostanie wyświetlony w okienku wyskakującym w wersji zapoznawczej.  Jeśli plik nagłówkowy nie istnieje, zostanie również być utworzona i umieszczone w projekcie.

   ![Utwórz deklarację / definicję wyniku](images/movedefinition_result.png)
