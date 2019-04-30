---
title: Ostrzeżenie LNK4204 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4204
helpviewer_keywords:
- LNK4204
ms.assetid: 14adda20-0cbe-407b-90f6-9f81c93530e2
ms.openlocfilehash: 790b0fa25bbf41c38b843e1a2ea757fdc0d10b9a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395108"
---
# <a name="linker-tools-warning-lnk4204"></a>Ostrzeżenie LNK4204 narzędzi konsolidatora

"filename" nie ma informacji debugowania dla przywołującego modułu; skonsolidowany obiektu bez informacji debugowania

Plik .pdb ma podpis błędne. Konsolidator będą w dalszym ciągu łącze obiektu bez informacji o debugowaniu. Chcesz ponownie skompilować przy użyciu pliku obiektu [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) opcji.

LNK4204 może wystąpić, jeśli niektórych obiektów biblioteki odnoszą się do pliku, który już nie istnieje. To może się zdarzyć, gdy ponownie skompilować rozwiązanie, np. Plik obiektu może być usunięty i nie zostanie ponownie skompilowany z powodu błędu kompilacji. W tym przypadku albo kompilacji z **/z7**, lub **/Fd**, aby zaktualizować obiektów do odwoływania się do pojedynczego pliku na biblioteki (który nie jest domyślna nazwa pliku .pdb).  Aby uzyskać więcej informacji, zobacz [/Fd (nazwa pliku bazy danych programu)](../../build/reference/fd-program-database-file-name.md).  Upewnij się, że .pdb zostaje zapisana wraz z biblioteki, za każdym razem, gdy jest on aktualizowany w systemie kontroli źródła.