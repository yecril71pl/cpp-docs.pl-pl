---
title: Błąd narzędzi konsolidatora LNK1000
ms.date: 06/18/2018
f1_keywords:
- LNK1000
helpviewer_keywords:
- LNK1000
ms.assetid: 86421b9a-460a-4285-8dce-9b8257d78122
ms.openlocfilehash: 48b976f6e996d0e076849dc9b20b4cedd47dfbcd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195425"
---
# <a name="linker-tools-error-lnk1000"></a>Błąd narzędzi konsolidatora LNK1000

> nieznany błąd; Zapoznaj się z dokumentacją dotyczącą opcji pomocy technicznej

Zanotuj sytuacje błędu, a następnie spróbuj wyizolować problem i utworzyć powtarzalny przypadek testowy. Aby uzyskać informacje o tym, jak zbadać i zgłosić te błędy, zobacz [Jak zgłosić problem z zestawem C++ narzędzi wizualnych lub dokumentacją](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).

Ten błąd może wystąpić, jeśli Mieszasz standardowe pliki nagłówkowe (na przykład Windows. h) i własne pliki. Dołącz prekompilowany nagłówek (jeśli istnieje), a następnie nagłówki standardowe, a następnie własne pliki nagłówkowe.
