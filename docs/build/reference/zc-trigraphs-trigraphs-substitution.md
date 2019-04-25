---
title: /Zc:trigraphs (Podstawianie trigramów)
ms.date: 03/06/2018
f1_keywords:
- /Zc
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
ms.openlocfilehash: 7a20123603030dfe719cd8990018f795df137981
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316005"
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

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości do uwzględnienia **/Zc: trigraphs** lub **/Zc:trigraphs-** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](zc-conformance.md)<br/>
[Trigramy](../../c-language/trigraphs.md)<br/>
