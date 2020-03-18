---
title: /Zc:trigraphs (Podstawianie trigramów)
ms.date: 03/06/2018
f1_keywords:
- /Zc:trigraphs
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
ms.openlocfilehash: 0e4c98e09551d39e3ff7978767b21f1d2c5bb318
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438648"
---
# <a name="zctrigraphs-trigraphs-substitution"></a>/Zc:trigraphs (Podstawianie trigramów)

Gdy **/Zc: trigraphs** jest określony, kompilator zastępuje sekwencję znaku trójznaków przy użyciu odpowiedniego znaku interpunkcji.

## <a name="syntax"></a>Składnia

> **/Zc: trigraphs**[ **-** ]

## <a name="remarks"></a>Uwagi

*Trójznaków* składa się z dwóch następujących po sobie znaków zapytania ("??"), po których następuje unikatowy trzeci znak. Standard języka C obsługuje trigraphs dla plików źródłowych, które używają zestawu znaków, który nie zawiera wygodnych reprezentacji graficznych dla niektórych znaków interpunkcyjnych. Na przykład gdy trigraphs są włączone, kompilator zastępuje "? = "trójznaków przy użyciu znaku" # ". Do języka C++ 14 trigraphs są obsługiwane w języku C. Standard C++ 17 usuwa trigraphs z C++ języka. W C++ kodzie, opcja kompilatora **/Zc: trigraphs** umożliwia podstawienie sekwencji trójznaków za pomocą odpowiedniego znaku interpunkcji. **/Zc: trigraphs-** wyłącza podstawianie trójznaków.

Opcja **/Zc: trigraphs** jest domyślnie wyłączona i nie ma to żadnego oddziaływania, gdy określono opcję [/permissive-](permissive-standards-conformance.md) .

Aby zapoznać się z listąC++ języka C/trigraphs i przykładem, który pokazuje, jak używać trigraphs, zobacz [trigraphs](../../c-language/trigraphs.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Właściwości konfiguracji** > strony właściwości **wiersza polecenia** **C++ C/**  > .

1. Zmodyfikuj właściwość **Opcje dodatkowe** , aby uwzględnić **/Zc: trigraphs** lub **/Zc: trigraphs-** , a następnie wybierz **przycisk OK**.

## <a name="see-also"></a>Zobacz też

[/Zc (Zgodność)](zc-conformance.md)<br/>
[Trigramy](../../c-language/trigraphs.md)<br/>
