---
title: "/ Zc: trigraphs (podstawianie trigramów) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: article
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
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5fdc5fc6432335e964a05185b7647b152a57d8f4
ms.sourcegitcommit: eeb2b5ad8d3d22514a7b9bd7d756511b69ae0ccf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="zctrigraphs-trigraphs-substitution"></a>/Zc:trigraphs (Podstawianie trigramów)

Gdy **/Zc: trigraphs** określono kompilator zastępuje sekwencja znaków — trigram przy użyciu odpowiedniego znak interpunkcyjny.

## <a name="syntax"></a>Składnia

> **/ Zc: trigraphs**[**-**]  

## <a name="remarks"></a>Uwagi

A *— trigram* składa się z dwóch następujących po sobie znaki zapytania ("?") następuje znak trzeci unikatowy. Standard języka C obsługuje trigramów dla plików źródłowych, które używają zestawu znaków, która nie zawiera graficzne przedstawienie wygodny dla niektórych znaków interpunkcyjnych. Na przykład, gdy trigramów są włączone, kompilator zastępuje "? = "— trigram za pomocą znaku"#". Za pomocą języka C ++ 14 trigramów są obsługiwane, jak C. C ++ 17 standardowe usuwa trigramów języka C++. W kodzie C++ **/Zc: trigraphs** — opcja kompilatora umożliwia zastąpienie sekwencji — trigram przez odpowiedni znak interpunkcyjny. **/Zc:trigraphs-** wyłącza — trigram podstawienia.

**/Zc: trigraphs** opcja jest domyślnie wyłączona i nie jest opcją wpływ, kiedy [/ ograniczająca-](permissive-standards-conformance.md) określono opcję.

Aby uzyskać listę trigramów C/C++ oraz przykład przedstawia sposób użycia trigramów, zobacz [Trigramów](../../c-language/trigraphs.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** strony właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości, aby uwzględnić **/Zc: trigraphs** lub **/Zc:trigraphs-** , a następnie wybierz **OK**.

## <a name="see-also"></a>Zobacz także

[/Zc (Zgodność)](../../build/reference/zc-conformance.md)<br/>
[Trigramy](../../c-language/trigraphs.md)<br/>
