---
title: Błąd krytyczny C1002
ms.date: 11/04/2016
f1_keywords:
- C1002
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
ms.openlocfilehash: 78edf886f34665f996497abe323a0ea5d3800c2d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204935"
---
# <a name="fatal-error-c1002"></a>Błąd krytyczny C1002

Kompilator nie ma miejsca na stercie w przebiegu 2

Kompilator wypełnił ilość pamięci dynamicznej podczas jej drugiego przebiegu, prawdopodobnie z powodu programu z zbyt dużą liczbą symboli lub złożonych wyrażeń.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Aby rozwiązać ten problem, można użyć następujących rozwiązań

1. Podziel plik źródłowy na kilka mniejszych plików.

1. Podział wyrażeń na mniejsze podwyrażenia.

1. Usuń inne programy lub sterowniki zużywające pamięć.
