---
title: Utwórz deklarację / definicję | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/19/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: 6b1cdcb2-765e-4b93-8cef-92b861f64eba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 21edf09eb78d339c06c709b06e8fe43ea72475c4
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808410"
---
# <a name="create-declaration--definition"></a>Utwórz deklarację / definicję
**Co:** pozwala natychmiast wygenerować deklaracji lub definicji funkcji.

**Kiedy:** ma funkcję, która wymaga deklaracji lub na odwrót.

**Dlaczego:** można ręcznie utworzyć deklarację/definicję, ale spowoduje to utworzenie go automatycznie, tworząc nagłówek/plik kodu, jeśli jest to wymagane.

**Jak:**

1. Umieść kursor tekstu lub myszy za pośrednictwem funkcji, którą chcesz Utwórz deklarację lub definicję.

   ![Wyróżniony kod](images/createdefinition_highlight.png)

1. Następnie wykonaj jedną z następujących czynności:
   * **Keyboard**
     * Naciśnij klawisz **Ctrl +.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Utwórz deklarację / definicję** z menu kontekstowego.
   * **Myszy**
     * Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Utwórz deklarację / definicję** z menu kontekstowego.

1. Funkcja deklaracji/definicji zostaną utworzone w pliku źródłowego lub nagłówek, który zostanie wyświetlony w okienku wyskakującym w wersji zapoznawczej.  Jeśli plik źródłowy lub nagłówka nie istnieje, zostanie również być utworzona i umieszczone w projekcie.

   ![Utwórz deklarację / definicję wyniku](images/createdefinition_result.png)
