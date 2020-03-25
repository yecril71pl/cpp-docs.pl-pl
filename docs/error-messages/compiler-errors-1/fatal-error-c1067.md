---
title: Błąd krytyczny C1067
ms.date: 11/04/2016
f1_keywords:
- C1067
helpviewer_keywords:
- C1067
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
ms.openlocfilehash: 3b016790220d409435ff7ea53c6f48899a9e8f1c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204350"
---
# <a name="fatal-error-c1067"></a>Błąd krytyczny C1067

ograniczenie kompilatora: przekroczono limit 64 KB rozmiaru rekordu typu

Ten błąd może wystąpić, jeśli symbol ma nazwę dekoracyjną przekraczającą 247 znaków.  Aby rozwiązać ten problem, Skróć nazwę symbolu.

Gdy kompilator generuje informacje debugowania, emituje rekordy typu w celu zdefiniowania typów napotkanych w kodzie źródłowym.  Na przykład wpisz rekordy zawierają proste struktury i listy argumentów funkcji.  Niektóre z tych rekordów typu mogą być dużymi listami.

Występuje limit 64 KB rozmiaru dowolnego rekordu typu.  W przypadku przekroczenia limitu 64 KB ten błąd wystąpi.

C1067 może również wystąpić, jeśli istnieje wiele symboli z długimi nazwami lub jeśli klasa, struktura lub Unia ma zbyt wiele elementów członkowskich.
