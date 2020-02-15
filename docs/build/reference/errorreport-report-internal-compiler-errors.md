---
title: /errorReport (Zgłaszaj wewnętrzne błędy kompilatora)
description: Dokumentacja opcji wiersza polecenia/errorReport językaC++ Microsoft C/kompilatora.
ms.date: 02/09/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.ErrorReporting
- /errorreport
helpviewer_keywords:
- /errorReport compiler option [C++]
- -errorReport compiler option [C++]
ms.assetid: 819828f8-b0a5-412c-9c57-bf822f17e667
ms.openlocfilehash: 8d4a3c4d5fd918973bbf8057e0c073c680e6995e
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257653"
---
# <a name="errorreport-report-internal-compiler-errors"></a>/errorReport (Zgłaszaj wewnętrzne błędy kompilatora)

> [!NOTE]
> Opcja **/errorreport** jest przestarzała. Począwszy od systemu Windows Vista, raportowanie błędów jest kontrolowane przez ustawienia [raportowanie błędów systemu Windows (wer)](/windows/win32/wer/windows-error-reporting) .

## <a name="syntax"></a>Składnia

> **/errorReport:** \[**none** \| **monit** \| **kolejki** \| **send** ]

## <a name="remarks"></a>Uwagi

Wewnętrzny błąd kompilatora (lodem) powstaje, gdy kompilator nie może przetworzyć pliku kodu źródłowego. W przypadku wystąpienia lodu kompilator nie produkuje pliku wyjściowego ani żadnych przydatnych diagnostyki, których można użyć do naprawienia kodu.

Argumenty **/errorreport** są zastępowane przez ustawienia usługi Raportowanie błędów systemu Windows. Kompilator automatycznie wysyła raporty o błędach wewnętrznych do firmy Microsoft, jeśli raportowanie jest włączone przez Raportowanie błędów systemu Windows. Nie jest wysyłany raport, jeśli jest wyłączony przez Raportowanie błędów systemu Windows.


### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać więcej informacji, [Zobacz C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Otwórz okno **Właściwości konfiguracji** > **C/C++**  > **zaawansowanej** strony właściwości.

1. Zmodyfikuj właściwość **raportowanie błędów** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ErrorReporting%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)\
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
