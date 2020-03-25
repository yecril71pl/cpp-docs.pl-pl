---
title: Ostrzeżenie LNK4204 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4204
helpviewer_keywords:
- LNK4204
ms.assetid: 14adda20-0cbe-407b-90f6-9f81c93530e2
ms.openlocfilehash: 98c53c9b998e9bd544c1cc72bd2b0c3fd2b0a418
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193865"
---
# <a name="linker-tools-warning-lnk4204"></a>Ostrzeżenie LNK4204 narzędzi konsolidatora

w pliku "filename" brakuje informacji debugowania dla przywołującego modułu; Łączenie obiektu bez informacji debugowania

Plik. pdb ma błędną sygnaturę. Konsolidator będzie nadal łączyć obiekt bez informacji o debugowaniu. Możesz chcieć ponownie skompilować plik obiektu przy użyciu opcji [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) .

LNK4204 narzędzi KONSOLIDATORA może wystąpić, jeśli niektóre obiekty w bibliotece odwołują się do pliku, który już nie istnieje. Może się to zdarzyć podczas ponownego kompilowania rozwiązania, na przykład: plik obiektu może zostać usunięty i nie można go ponownie skompilować z powodu błędu kompilacji. W takim przypadku Kompiluj z **/Z7**lub **/FD**, aby zaktualizować obiekty w celu odwoływania się do pojedynczego pliku na bibliotekę (nie jest to domyślna nazwa pliku. pdb).  Aby uzyskać więcej informacji, zobacz [/FD (nazwa pliku bazy danych programu)](../../build/reference/fd-program-database-file-name.md).  Upewnij się, że plik. pdb jest zapisywany z biblioteką za każdym razem, gdy jest aktualizowana w systemie kontroli źródła.
