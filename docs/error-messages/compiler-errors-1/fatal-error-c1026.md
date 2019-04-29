---
title: Błąd krytyczny C1026
ms.date: 11/04/2016
f1_keywords:
- C1026
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
ms.openlocfilehash: b1a659967a9a62cb79e1084f7d1fa1729bae14da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347132"
---
# <a name="fatal-error-c1026"></a>Błąd krytyczny C1026

przepełnienie stosu analizatora składni, zbyt złożony program

Miejsca wymaganego do analizowania program spowodowało przepełnienie stosu kompilatora.

Zmniejsz złożoność wyrażenia przez:

- Zmniejszenie zagnieżdżenia w `for` i `switch` instrukcji. Umieść głębiej zagnieżdżonych instrukcji w funkcji.

- Podzielenie długich wyrażeń obejmujących operatory przecinkami lub wywołania funkcji.