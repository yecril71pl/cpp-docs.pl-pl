---
title: '/ Zc: trigraphs (podstawianie Trigramów) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce8c9d13fa062ddac0f31eac0e20fba1266c7a8c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707736"
---
# <a name="zctrigraphs-trigraphs-substitution"></a>/Zc:trigraphs (Podstawianie trigramów)

Gdy **/Zc: trigraphs** jest określony, kompilator zamienia na sekwencję znaków — trigram przy użyciu odpowiedniego znaku interpunkcji.

## <a name="syntax"></a>Składnia

> **/ Zc: trigraphs**[**-**]

## <a name="remarks"></a>Uwagi

A *trójznaków* składa się z dwóch następujących po sobie znaki zapytania ("??") następuje znak trzeci unikatowy. Standard języka C obsługuje trójznaków dla plików źródłowych, które używają zestawu znaków, który nie zawiera wygodnych reprezentacji graficznych dla niektórych znaków interpunkcyjnych. Na przykład, gdy trójznaków są włączone, kompilator zastępuje "? = "trójznaków za pomocą znaku"#". Za pomocą języka C ++ 14 trójznaków są obsługiwane w C. C ++ 17 standardowa usuwa trójznaków z języka C++. W przypadku kodu C++ **/Zc: trigraphs** — opcja kompilatora umożliwia zastąpienie sekwencje trójznakowe przez odpowiedni znak interpunkcyjny. **/Zc:trigraphs-** wyłącza podstawienia trójznaków.

**/Zc: trigraphs** opcja jest domyślnie wyłączona i nie dotyczy, kiedy [/ permissive-](permissive-standards-conformance.md) określono opcję.

Aby uzyskać listę trójznaków C/C++ i przykładowi, który pokazuje, jak używać trójznaków, zobacz [Trójznaków](../../c-language/trigraphs.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości do uwzględnienia **/Zc: trigraphs** lub **/Zc:trigraphs-** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](../../build/reference/zc-conformance.md)<br/>
[Trigramy](../../c-language/trigraphs.md)<br/>
