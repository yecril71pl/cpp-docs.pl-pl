---
title: Błąd narzędzi konsolidatora LNK1000 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 06/18/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1000
dev_langs:
- C++
helpviewer_keywords:
- LNK1000
ms.assetid: 86421b9a-460a-4285-8dce-9b8257d78122
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a01db36200995813ec4b6862e9ddd04c6f069ba
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238685"
---
# <a name="linker-tools-error-lnk1000"></a>Błąd narzędzi konsolidatora LNK1000

> Nieznany błąd; zobacz dokumentację, aby uzyskać informacje o opcjach pomocy technicznej

Należy zwrócić uwagę okoliczności błędu, a następnie spróbuj ustalić przyczynę problemu i Utwórz przypadek testowy odtworzenia. Aby uzyskać informacje na temat zbadania i raportuje te błędy, zobacz [jak zgłosić problem z zestawu narzędzi Visual C++ lub dokumentacją](../../how-to-report-a-problem-with-the-visual-cpp-toolset.md).

Błąd ten może wystąpić, jeśli mieszać plików standardowy nagłówek (na przykład Windows.h) i pliki. Prekompilowanego nagłówka, należy uwzględnić, jeśli dowolne, najpierw, a następnie standardowych nagłówków, a następnie pliki nagłówka.