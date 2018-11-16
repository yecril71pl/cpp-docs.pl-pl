---
title: Przenieś lokalizację definicji
ms.date: 11/16/2016
ms.assetid: c6d507ac-c61e-4da2-95c8-d504b42e2520
ms.openlocfilehash: 7957e18732dfae92b7b3ae9cf7ecea441fc3a6b4
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693208"
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
