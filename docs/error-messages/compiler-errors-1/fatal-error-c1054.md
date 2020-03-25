---
title: Błąd krytyczny C1054
ms.date: 11/04/2016
f1_keywords:
- C1054
helpviewer_keywords:
- C1054
ms.assetid: 9cfb7307-b22a-4418-b7c0-2621b0ab5b1b
ms.openlocfilehash: d094d0892d43a5f9894f03538f72e59b57bad6db
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204467"
---
# <a name="fatal-error-c1054"></a>Błąd krytyczny C1054

ograniczenie kompilatora: inicjatory są zagnieżdżone zbyt głęboko

Kod przekracza limit zagnieżdżenia dla inicjatorów (10-15 poziomów, w zależności od kombinacji typów, które są inicjowane).

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać ten problem, można użyć następujących rozwiązań

1. Uprość typy danych, które są inicjowane w celu zmniejszenia zagnieżdżenia.

1. Inicjuj zmienne w oddzielnych instrukcjach po deklaracji.
