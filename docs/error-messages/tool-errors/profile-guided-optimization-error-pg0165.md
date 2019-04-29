---
title: Błąd optymalizacji sterowanej profilem PG0165
ms.date: 11/04/2016
f1_keywords:
- PG0165
helpviewer_keywords:
- PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
ms.openlocfilehash: f39bbe6540ebec10cd25c41ac2fe9f2acfca9b13
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359738"
---
# <a name="profile-guided-optimization-error-pg0165"></a>Błąd optymalizacji sterowanej profilem PG0165

Odczytywanie "Filename.pgd": "Nie jest obsługiwana wersja pliku PGD (niezgodność wersji)".

Pliki PGD są specyficzne dla kompilatora określonego zestawu narzędzi. Ten błąd jest generowany, gdy używasz innego kompilatora niż ten używany do *Filename*.pgd. Ten błąd wskazuje, że ten zestaw narzędzi kompilatora nie mogą używać danych z *Filename*.pgd do optymalizacji bieżącego programu.

Aby rozwiązać ten problem, należy ponownie wygenerować *Filename*.pgd przy użyciu bieżącego zestawu narzędzi kompilatora.