---
title: Ostrzeżenie LNK4102 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4102
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
ms.openlocfilehash: fda1fdb03a7629894f846bb20ed84df519239327
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183309"
---
# <a name="linker-tools-warning-lnk4102"></a>Ostrzeżenie LNK4102 narzędzi konsolidatora

Eksportowanie usuwania destruktora "name"; obraz może nie działać poprawnie

Program podjął próbę wyeksportowania destruktora usuwającego. Powstające usunięcie może wystąpić w granicach biblioteki DLL, w taki sposób, że proces może zwolnić nieposiadaną pamięć. Upewnij się, że podany symbol nie znajduje się na liście w pliku def i że symbol nie jest wymieniony jako argument opcji **/Import** lub **/Export** w wierszu polecenia konsolidatora.

W przypadku ponownego kompilowania biblioteki wykonawczej C można zignorować ten komunikat.
