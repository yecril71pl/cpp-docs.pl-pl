---
title: /errorReport (Zgłaszaj wewnętrzne błędy kompilatora)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.ErrorReporting
- /errorreport
helpviewer_keywords:
- /errorReport compiler option [C++]
- -errorReport compiler option [C++]
ms.assetid: 819828f8-b0a5-412c-9c57-bf822f17e667
ms.openlocfilehash: 52909cb42180bf8b778d73fd709be05faf3f5714
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271791"
---
# <a name="errorreport-report-internal-compiler-errors"></a>/errorReport (Zgłaszaj wewnętrzne błędy kompilatora)

Pozwala zapewnić wewnętrznych kompilatora-informacje o błędzie (ICE) bezpośrednio do firmy Microsoft.

## <a name="syntax"></a>Składnia

```
/errorReport:[ none | prompt | queue | send ]
```

## <a name="arguments"></a>Argumenty

**Brak**<br/>
Raporty o błędach wewnętrznych kompilatora nie będą zbierane ani wysyłane do firmy Microsoft.

**wiersz**<br/>
Monituje o wysłanie raportu po pojawieniu się błędu wewnętrznego kompilatora. **wiersz** jest domyślną kolekcją podczas kompilowania aplikacji w środowisku programistycznym.

**kolejki**<br/>
Kolejkuje raport o błędach. Po zalogowaniu się przy użyciu uprawnień administratora, wyświetlane jest okno, dzięki czemu możesz zgłaszać błędów od czasu ostatniego zostały zarejestrowane w (użytkownik nie jest monitowany o wysłanie raportu błędów więcej niż raz na trzy dni). **kolejka** jest domyślną kolekcją podczas kompilowania aplikacji w wierszu polecenia.

**Wyślij**<br/>
Automatycznie wysyła raporty błędów wewnętrznych kompilatora do firmy Microsoft, jeśli raportowanie został włączony przez ustawienia systemu Windows Error Reporting.

## <a name="remarks"></a>Uwagi

Wewnętrzny błąd kompilatora (ICE) wyniki, gdy kompilator nie może przetworzyć pliku kodu źródłowego. W przypadku ICE kompilator nie generuje plik wyjściowy lub przydatne diagnostyki, która służy do poprawienia kodu.

We wcześniejszych wersjach gdy masz ICE było zachęca do wywołania techniczną firmy Microsoft, aby zgłosić problem. Za pomocą **/errorreport**, możesz podać informacje ICE bezpośrednio do firmy Microsoft. Twoje raporty o błędach może zwiększyć kompilatora w przyszłych wersjach.

Zdolność użytkownika do wysyłania raportów zależy od uprawnienia zasad komputera i użytkownika.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **zaawansowane** stronę właściwości.

1. Modyfikowanie **raportowanie błędów** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ErrorReporting%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
