---
title: Błąd narzędzi konsolidatora LNK1188
ms.date: 11/04/2016
f1_keywords:
- LNK1188
helpviewer_keywords:
- LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
ms.openlocfilehash: b18a93c7434ee3d66f42829f373bd916a65369bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195178"
---
# <a name="linker-tools-error-lnk1188"></a>Błąd narzędzi konsolidatora LNK1188

BADFIXUPSECTION:: nieprawidłowy cel naprawy "symbol"; dozwolona sekcja o zerowej długości

W ramach linku VxD element docelowy relokacji nie ma sekcji. W przypadku LINK386 (starszej wersji) rekord grupy OMF (wygenerowany przez dyrektywę grupy MASM) mógł zostać użyty do połączenia sekcji o zerowej długości z inną sekcją o niezerowej długości. Format COFF nie obsługuje dyrektywy GROUP i sekcji o zerowej długości. Gdy LINK automatycznie konwertuje ten typ obiektów OMF na COFF, ten błąd może wystąpić.
