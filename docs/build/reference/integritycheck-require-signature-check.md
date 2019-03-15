---
title: /INTEGRITYCHECK (Wymagaj sprawdzania podpisu)
ms.date: 11/04/2016
ms.assetid: 9e738825-2c98-40cd-8ad2-5d0d9c14893e
ms.openlocfilehash: 446ebe3afc06b8db8cc9f36b289c1e5c3ef5f117
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813685"
---
# <a name="integritycheck-require-signature-check"></a>/INTEGRITYCHECK (Wymagaj sprawdzania podpisu)

Określa, czy podpis cyfrowy obrazu binarnego musi być zaznaczone w czasie ładowania.

```
/INTEGRITYCHECK[:NO]
```

## <a name="remarks"></a>Uwagi

Domyślnie **/INTEGRITYCHECK** jest wyłączona.

**/INTEGRITYCHECK** zestawy opcji — w nagłówku PE pliku DLL lub pliku wykonywalnego — Flaga, dla Menedżera pamięci sprawdzić podpis cyfrowy w celu załadowania obrazu w Windows. Ta opcja musi być ustawiona dla 32-bitowych i 64-bitowych bibliotek DLL, które implementują kod trybu jądra ładowany przez niektóre funkcje Windows i jest zalecana dla wszystkich sterowników urządzeń w Windows Vista, Windows 7, Windows 8, Windows Server 2008 i Windows Server 2012. Wersje Windows przed Windows Vista, ignorują tę flagę. Aby uzyskać więcej informacji, zobacz [wymuszone podpisywanie integralności z przenośny plik wykonywalny () plików PE](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx).

### <a name="to-set-this-linker-option-in-visual-studio"></a>Aby ustawić tę opcję konsolidatora w programie Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Rozwiń **właściwości konfiguracji** węzła.

1. Rozwiń **konsolidatora** węzła.

1. Wybierz **wiersza polecenia** stronę właściwości.

1. W **dodatkowe opcje**, wprowadź `/INTEGRITYCHECK` lub `/INTEGRITYCHECK:NO`.

## <a name="see-also"></a>Zobacz także

[Odwołania konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)<br/>
[Wymuszone podpisywanie integralności z przenośny plik wykonywalny () plików PE](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)<br/>
[Podpisywanie instruktażu kodu trybu jądra](https://msdn.microsoft.com/windows/hardware/gg487328.aspx)<br/>
[AppInit dll w Windows 7 i Windows Server 2008](https://msdn.microsoft.com/windows/hardware/gg463040.aspx)
