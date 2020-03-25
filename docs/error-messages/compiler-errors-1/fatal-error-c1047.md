---
title: Błąd krytyczny C1047
ms.date: 11/04/2016
f1_keywords:
- C1047
helpviewer_keywords:
- C1047
ms.assetid: e1bbbc6b-a5bc-4c23-8203-488120a0ec78
ms.openlocfilehash: 5ab98c46d60d15cdcb6de22aa922d62453d41880
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204495"
---
# <a name="fatal-error-c1047"></a>Błąd krytyczny C1047

Obiekt lub plik biblioteki "File" został utworzony za pomocą starszego kompilatora niż inne obiekty; ponowne kompilowanie starych obiektów i bibliotek

C1047 jest spowodowany tym, że pliki obiektów lub biblioteki skompilowane za pomocą **/LTCG** są połączone ze sobą, ale gdzie te pliki lub biblioteki zostały skompilowane C++ z różnymi wersjami zestawu narzędzi wizualnych.

Taka sytuacja może wystąpić, jeśli zaczniesz korzystać z nowej wersji kompilatora, ale nie przeprowadzaj czystej odbudowy istniejących plików lub bibliotek obiektów.

Aby rozwiązać C1047, Skompiluj ponownie wszystkie pliki lub biblioteki obiektów.
