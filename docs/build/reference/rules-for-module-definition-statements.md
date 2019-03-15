---
title: Zasady dla instrukcji definicji modułu
ms.date: 11/04/2016
f1_keywords:
- .def
helpviewer_keywords:
- module definition files, statement syntax
- module definition files
ms.assetid: f65cd3a7-65d7-4d06-939f-a8b1ecd50f2d
ms.openlocfilehash: f6269ad2d5bf3952e485f2ca5e5d1f411c5f1e0c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57821277"
---
# <a name="rules-for-module-definition-statements"></a>Zasady dla instrukcji definicji modułu

Następujące reguły składni dotyczą wszystkie instrukcje w pliku .def. Inne zasady, które są stosowane do instrukcji określonych są opisane za pomocą każdej instrukcji.

- Instrukcje i identyfikatory określone przez użytkownika słowa atrybut uwzględniają wielkość liter.

- Długie nazwy zawierające spacje lub średników (;) plików muszą być ujęte w znaki cudzysłowu (").

- Do oddzielania słowem kluczowym instrukcji z jej argumentów i oddzielania instrukcji od siebie nawzajem, należy użyć jednego lub więcej miejsca do magazynowania, karty lub znakami nowego wiersza. Dwukropek (:) lub znak równości (=), która określa argument jest otoczona przez zero lub więcej miejsca do magazynowania, karty lub znakami nowego wiersza.

- A **nazwa** lub **biblioteki** instrukcji, jeśli używany, musi poprzedzać wszystkie inne instrukcje.

- **Sekcje** i **EKSPORTY** instrukcji może występować więcej niż jeden raz w pliku .def. Każda instrukcja może zająć wiele specyfikacje, które muszą być oddzielone jeden lub więcej miejsca do magazynowania, karty lub znakami nowego wiersza. Instrukcja — słowo kluczowe musi pojawić się jeden raz przed pierwszą specyfikację i można powtarzać przed każdego dodatkowego specyfikacji.

- Wiele instrukcji mieć równoważne opcji wiersza polecenia łącza. Zobacz opis odpowiedniej opcji LINK, aby uzyskać więcej informacji.

- Komentarze w pliku .def zostały oznaczone za pomocą średnika (;) na początku każdego wiersza komentarza. Komentarz nie można udostępniać wiersza po instrukcji, ale może być wyświetlany między specyfikacjami w wielowierszowym instrukcji. (**Sekcje** i **EKSPORTY** są instrukcje wielowierszowy.)

- Liczbowe argumenty są określone w podstawie 10 lub szesnastkowego.

- Jeśli argument ciągu pasuje [słowa zarezerwowanego](reserved-words.md), muszą być ujęte w podwójny cudzysłów (").

## <a name="see-also"></a>Zobacz także

[Pliki definicji modułu (.Def)](module-definition-dot-def-files.md)
