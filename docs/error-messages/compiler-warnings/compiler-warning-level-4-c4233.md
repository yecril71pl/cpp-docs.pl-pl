---
title: "Kompilatora (poziom 4) ostrzeżenie C4233 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 10/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4233
dev_langs: C++
helpviewer_keywords: C4233
ms.assetid: 9aa51fc6-8ef3-43b5-bafb-c9333cf60de3
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 16e32686451ba7ce0c9a633878f1158a8457163a
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="compiler-warning-level-4-c4233"></a>Kompilator C4233 ostrzegawcze (poziom 4)

> użyto niestandardowego rozszerzenia: "*— słowo kluczowe*" obsługiwane tylko w języku C++ nie C — słowo kluczowe

Kompilator skompilowany kodu źródłowego C, a nie C++ i użyto słowa kluczowego, który jest prawidłowy tylko w języku C++. Kompilator kompiluje pliku źródłowego c, jeśli rozszerzenie pliku źródłowego jest .c lub używasz [/TC](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md).

To ostrzeżenie zostanie automatycznie podwyższony do wystąpił błąd. Jeśli chcesz zmienić to zachowanie, użyj [ostrzeżenie #pragma](../../preprocessor/warning.md). Na przykład aby C4233 na poziom 4 ostrzeżenie problem, Dodaj ten wiersz do pliku kodu źródłowego:

```cpp
#pragma warning(4:4233)
```
