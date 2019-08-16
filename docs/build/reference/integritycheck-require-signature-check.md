---
title: /INTEGRITYCHECK (Wymagaj sprawdzania podpisu)
ms.date: 11/04/2016
ms.assetid: 9e738825-2c98-40cd-8ad2-5d0d9c14893e
ms.openlocfilehash: 1732c612501b66753635b272f94764975c555f75
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492848"
---
# <a name="integritycheck-require-signature-check"></a>/INTEGRITYCHECK (Wymagaj sprawdzania podpisu)

Określa, że podpis cyfrowy obrazu binarnego musi być sprawdzany w czasie ładowania.

```
/INTEGRITYCHECK[:NO]
```

## <a name="remarks"></a>Uwagi

Domyślnie **/INTEGRITYCHECK** jest wyłączona.

Zestawy opcji **/INTEGRITYCHECK** — w nagłówku PE pliku DLL lub pliku wykonywalnego — flagi Menedżera pamięci do sprawdzenia podpisu cyfrowego w celu załadowania obrazu w systemie Windows. Ta opcja musi być ustawiona zarówno dla 32-bitowych, jak i 64-bitowych bibliotek DLL, które implementują kod trybu jądra załadowanego przez niektóre funkcje systemu Windows, i jest zalecana dla wszystkich sterowników urządzeń w systemach Windows Vista, Windows 7, Windows 8, Windows Server 2008 i Windows Server 2012. W wersjach systemu Windows starszych niż Windows Vista zignoruj tę flagę. Aby uzyskać więcej informacji, zobacz wymuszone podpisywanie [integralności przenośnych plików wykonywalnych (PE)](https://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx).

### <a name="to-set-this-linker-option-in-visual-studio"></a>Aby ustawić tę opcję konsolidatora w programie Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać więcej informacji, [Zobacz C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Rozwiń węzeł **Właściwości konfiguracji** .

1. Rozwiń węzeł **konsolidatora** .

1. Wybierz stronę właściwości **wiersza polecenia** .

1. W obszarze **Opcje dodatkowe**wprowadź `/INTEGRITYCHECK` lub `/INTEGRITYCHECK:NO`.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)<br/>
[Wymuszone podpisywanie integralności przenośnych plików wykonywalnych (PE)](https://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)<br/>
[Wymagania dotyczące podpisywania kodu trybu jądra](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-)<br/>
[AppInit dll i bezpieczny rozruch](/windows/win32/dlls/secure-boot-and-appinit-dlls)
