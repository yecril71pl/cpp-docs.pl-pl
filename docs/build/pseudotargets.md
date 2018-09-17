---
title: Pseudo cele | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- makefiles, pseudotargets
- pseudotargets and NMAKE
- NMAKE program, pseudotargets
- timestamps, makefile pseudotargets
- NMAKE program, targets
ms.assetid: c8c479dc-0129-4186-8366-bc6251f2b494
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 56c0c0c93163759b604352a6e623f15726b8e7ec
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715835"
---
# <a name="pseudotargets"></a>Pseudo cele

Pseudotarget jest używany zamiast nazwy pliku w wierszu zależności etykietę. Jest interpretowany jako plik, który nie istnieje i dlatego jest nieaktualna. NMAKE przyjęto założenie, że sygnatura czasowa pseudotarget jest najbardziej aktualną wszystkie jego zależności. Jeśli ma nie zależności, przyjmowana jest bieżący czas. Jeśli pseudotarget jest używany jako obiekt docelowy, wykonywane są zawsze jego poleceń. Pseudotarget, używane jako zależnych od ustawień lokalnych muszą również zostać wyświetlony jako cel w innym zależności. Jednak tej zależności nie musi być blokiem poleceń.

Nazwy pseudotarget zgodne reguły Składnia nazwy pliku dla celów. Jednakże jeśli nazwa nie jest rozszerzeniem (czyli nie zawiera okresu), może przekroczyć ograniczenie 8 znaków w nazwach plików i może mieć maksymalnie 256 znaków.

## <a name="see-also"></a>Zobacz też

[Docelowe elementy](../build/targets.md)