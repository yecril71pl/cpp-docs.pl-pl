---
title: /Zc:trigraphs (Podstawianie trigramów)
description: Opcja kompilatora języka Microsoft C++, która kontroluje wsparcie zgodności dla trigraphs.
ms.date: 07/25/2020
f1_keywords:
- /Zc:trigraphs
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
ms.openlocfilehash: e24f3d2f0064c3acc04b4c3774f47f6e442d5ddd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211856"
---
# <a name="zctrigraphs-trigraphs-substitution"></a>`/Zc:trigraphs`(Trigraphs podstawienia)

Gdy **`/Zc:trigraphs`** jest określony, kompilator zastępuje sekwencję znaków trójznaków przy użyciu odpowiedniego znaku interpunkcji.

## <a name="syntax"></a>Składnia

> **`/Zc:trigraphs`**[**`-`**]

## <a name="remarks"></a>Uwagi

*Trójznaków* składa się z dwóch następujących po sobie znaków zapytania ( **`??`** ), po których następuje unikatowy trzeci znak. Standard języka C obsługuje trigraphs dla plików źródłowych, które używają zestawu znaków, który nie zawiera wygodnych reprezentacji graficznych dla niektórych znaków interpunkcyjnych. Na przykład gdy trigraphs są włączone, kompilator zastępuje **`??=`** trójznaków przy użyciu **`#`** znaku. Do języka C++ 14 trigraphs są obsługiwane w języku C. Standard C++ 17 usuwa trigraphs z języka C++. W kodzie C++ **`/Zc:trigraphs`** Opcja kompilatora umożliwia podstawienie sekwencji trójznaków przez odpowiedni znak interpunkcji. **`/Zc:trigraphs-`** wyłącza podstawianie trójznaków.

**`/Zc:trigraphs`** Opcja jest domyślnie wyłączona, a opcja nie ma wpływać, gdy [`/permissive-`](permissive-standards-conformance.md) opcja jest określona.

Aby uzyskać listę trigraphs C/C++ i przykład, który pokazuje, jak używać trigraphs, zobacz [trigraphs](../../c-language/trigraphs.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja wiersza polecenia**C/C++**  >  **Command Line** .

1. Zmodyfikuj właściwość **Opcje dodatkowe** , aby uwzględnić **`/Zc:trigraphs`** lub **`/Zc:trigraphs-`** , a następnie wybierz przycisk **OK**.

## <a name="see-also"></a>Zobacz także

[`/Zc`Zgodności](zc-conformance.md)<br/>
[Trigramy](../../c-language/trigraphs.md)
