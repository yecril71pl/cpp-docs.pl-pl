---
title: Operatory preprocesora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor operators
- operators [C++], preprocessor
ms.assetid: 884126d1-0ce2-48b6-9e06-8a2d7c4a9656
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c1bc364f0b24ed0f2e561ff9f452018faf2cfab6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066464"
---
# <a name="preprocessor-operators"></a>Operatory preprocesora
Cztery operatory specyficzne dla preprocesora są używane w kontekście `#define` — dyrektywa (zobacz poniżej, aby uzyskać podsumowanie). W trzech kolejnych sekcjach omówiono operatory tworzenia ciągu, charizing i wklejania tokenu. Instrukcje dotyczące `defined` operatora, zobacz [#if, #elif #else i #endif, dyrektywy](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md).

|Operator|Akcja|
|--------------|------------|
|[Operator tworzenia ciągów (#)](../preprocessor/stringizing-operator-hash.md)|Powoduje, że odpowiednie argumenty rzeczywiste do być ujęta w znaki podwójnego cudzysłowu|
|[Charizing operator (#@)](../preprocessor/charizing-operator-hash-at.md)|Powoduje, że odpowiadający argument do być ujęta w znaki pojedynczego cudzysłowu i powinien być traktowany jako znak (Microsoft Specific)|
|[Operator wklejania tokenu (##)](../preprocessor/token-pasting-operator-hash-hash.md)|Zezwala na tokeny używane jako argumenty rzeczywiste ma zostać połączony w celu utworzenia innych tokenów|
|[defined-operator](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|Upraszcza zapisywanie złożonego wyrażenia w niektórych dyrektyw — makro|

## <a name="see-also"></a>Zobacz też

[Dyrektywy preprocesora](../preprocessor/preprocessor-directives.md)<br/>
[Wstępnie zdefiniowane makra](../preprocessor/predefined-macros.md)<br/>
[Dokumentacja preprocesora języka C/C++](../preprocessor/c-cpp-preprocessor-reference.md)