---
title: Ostrzeżenie LNK4102 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4102
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
ms.openlocfilehash: 0f9c8649988dd3056e98730ac4b02022a8c9dd51
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327265"
---
# <a name="linker-tools-warning-lnk4102"></a>Ostrzeżenie LNK4102 narzędzi konsolidatora

Eksport destruktora "name"; Usuwanie Obraz może nie działać poprawnie

Program próbował wyeksportować usuwanie destruktora. Wynikowy usuwania może wystąpić granicę biblioteki DLL tak, aby proces może zwolnić pamięć, która nie jest właścicielem. Upewnij się, że dany symbol nie znajduje się w pliku .def i że symbol nie jest wymieniony jako argument **/IMPORT** lub **/EXPORT** opcji wiersza polecenia konsolidatora.

Do odbudowywania biblioteki wykonawczej języka C, możesz zignorować ten komunikat.