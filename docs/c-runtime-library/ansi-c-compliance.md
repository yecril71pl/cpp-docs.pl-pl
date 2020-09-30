---
title: Zgodność ANSI-C
description: Omówienie konwencji nazewnictwa środowiska uruchomieniowego języka Microsoft C dla zgodności ze standardem ANSI C.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Ansi
helpviewer_keywords:
- underscores, leading
- compatibility [C++], ANSI C
- compliance with ANSI C
- conventions [C++], Microsoft extensions
- underscores
- naming conventions [C++], Microsoft library
- ANSI [C++], C standard
- Microsoft extensions naming conventions
ms.assetid: 6be271bf-eecf-491a-a928-0ee2dd60e3b9
ms.openlocfilehash: 39a3f9299be7dbef4783faa8e6d08fe6ad8461f5
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590306"
---
# <a name="ansi-c-compliance"></a>Zgodność ANSI-C

Konwencja nazewnictwa dla wszystkich identyfikatorów specyficznych dla firmy Microsoft w systemie czasu wykonywania (takich jak funkcje, makra, stałe, zmienne i definicje typów) jest zgodna ze standardem ANSI. W tej dokumentacji każda funkcja czasu wykonywania zgodna ze standardami ANSI/ISO C jest zapisywana jako zgodna ze standardem ANSI. Aplikacje zgodne ze standardem ANSI powinny używać tylko tych funkcji zgodnych ze standardem ANSI.

Nazwy funkcji specyficznych dla firmy Microsoft i zmiennych globalnych zaczynają się pojedynczym podkreśleniem. Te nazwy można przesłonić tylko lokalnie, w ramach zakresu kodu. Na przykład podczas dołączania plików nagłówka Microsoft Run-Time można nadal lokalnie przesłonić funkcję specyficzną dla firmy Microsoft o nazwie `_open` przez zadeklarowanie zmiennej lokalnej o tej samej nazwie. Nie można jednak użyć tej nazwy dla własnej funkcji globalnej lub zmiennej globalnej.

Nazwy makr specyficznych dla firmy Microsoft i stałe manifestu zaczynają się od dwóch znaków podkreślenia lub z pojedynczym wiodącym podkreśleniem bezpośrednio po Wielkiej litery. Zakres tych identyfikatorów jest bezwzględny. Na przykład nie można użyć identyfikatora specyficznego dla firmy Microsoft **_UPPER** z tego powodu.

## <a name="see-also"></a>Zobacz też

[Zgodność](../c-runtime-library/compatibility.md)
