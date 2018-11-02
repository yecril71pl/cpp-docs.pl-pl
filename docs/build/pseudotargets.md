---
title: Pseudo cele
ms.date: 11/04/2016
helpviewer_keywords:
- makefiles, pseudotargets
- pseudotargets and NMAKE
- NMAKE program, pseudotargets
- timestamps, makefile pseudotargets
- NMAKE program, targets
ms.assetid: c8c479dc-0129-4186-8366-bc6251f2b494
ms.openlocfilehash: bf0f1e2feb91611222ade366a7644e89cbe22600
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541079"
---
# <a name="pseudotargets"></a>Pseudo cele

Pseudotarget jest używany zamiast nazwy pliku w wierszu zależności etykietę. Jest interpretowany jako plik, który nie istnieje i dlatego jest nieaktualna. NMAKE przyjęto założenie, że sygnatura czasowa pseudotarget jest najbardziej aktualną wszystkie jego zależności. Jeśli ma nie zależności, przyjmowana jest bieżący czas. Jeśli pseudotarget jest używany jako obiekt docelowy, wykonywane są zawsze jego poleceń. Pseudotarget, używane jako zależnych od ustawień lokalnych muszą również zostać wyświetlony jako cel w innym zależności. Jednak tej zależności nie musi być blokiem poleceń.

Nazwy pseudotarget zgodne reguły Składnia nazwy pliku dla celów. Jednakże jeśli nazwa nie jest rozszerzeniem (czyli nie zawiera okresu), może przekroczyć ograniczenie 8 znaków w nazwach plików i może mieć maksymalnie 256 znaków.

## <a name="see-also"></a>Zobacz też

[Docelowe elementy](../build/targets.md)