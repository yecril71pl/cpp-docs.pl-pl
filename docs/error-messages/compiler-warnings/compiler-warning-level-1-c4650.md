---
title: Ostrzeżenie kompilatora (poziom 1) C4650
ms.date: 11/04/2016
f1_keywords:
- C4650
helpviewer_keywords:
- C4650
ms.assetid: 3190b3e3-dcd6-4846-939b-f900ab652b2a
ms.openlocfilehash: e57f1d9acba4a8734339f3b8e538120abe542efc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199571"
---
# <a name="compiler-warning-level-1-c4650"></a>Ostrzeżenie kompilatora (poziom 1) C4650

informacje debugowania nie są w prekompilowanym nagłówku; dostępne są tylko symbole globalne z nagłówka

Prekompilowany plik nagłówkowy nie został skompilowany przy użyciu symbolicznych informacji debugowania firmy Microsoft.

W przypadku połączenia utworzony plik wykonywalny lub biblioteka dołączany dynamicznie nie będzie zawierał informacji o debugowaniu dla symboli lokalnych zawartych w prekompilowanym nagłówku.

To ostrzeżenie można uniknąć przez ponowne skompilowanie prekompilowanego pliku nagłówkowego za pomocą opcji wiersza polecenia [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) .
