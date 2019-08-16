---
title: /DELAY (Ustawienia opóźnienia importowania ładowania)
ms.date: 11/04/2016
f1_keywords:
- /delay
- VC.Project.VCLinkerTool.DelayNoBind
- VC.Project.VCLinkerTool.SupportUnloadOfDelayLoadedDLL
- VC.Project.VCLinkerTool.DelayUnload
helpviewer_keywords:
- delayed loading of DLLs, /DELAY option
- DELAY linker option
- /DELAY linker option
- -DELAY linker option
ms.assetid: 9334b332-cc58-4dae-b10f-a4c75972d50c
ms.openlocfilehash: ef6f5f768cf86f470d1322fa2a7bee6db794c2ef
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493007"
---
# <a name="delay-delay-load-import-settings"></a>/DELAY (Ustawienia opóźnienia importowania ładowania)

```
/DELAY:UNLOAD
/DELAY:NOBIND
```

## <a name="remarks"></a>Uwagi

Opcja/DELAY steruje [opóźnionym ładowaniem](linker-support-for-delay-loaded-dlls.md) bibliotek DLL:

- Kwalifikator UNLOAD informuje funkcję pomocnika ładowania opóźnień, aby obsługiwała jawne zwolnienie biblioteki DLL. Tabela adresów importu (IAT) jest resetowana do oryginalnej postaci, która unieważnia wskaźniki IAT i powoduje ich zastąpienie.

   Jeśli nie wybierzesz opcji ZWOLNIj, żadne wywołanie do [FUnloadDelayLoadedDLL](explicitly-unloading-a-delay-loaded-dll.md) zakończy się niepowodzeniem.

- Kwalifikator NOBIND informuje konsolidator, aby nie zawierał IAT możliwego do powiązania w końcowym obrazie. Wartość domyślna to utworzenie IAT możliwego do powiązania dla bibliotek DLL ładowanych z opóźnieniem. Obraz wyników nie może być powiązany statycznie. (Obrazy z IATsmi możliwymi do powiązania mogą być statycznie powiązane przed wykonaniem). Zobacz [/bind](bind.md).

   Jeśli biblioteka DLL jest powiązana, funkcja pomocnika podejmie próbę użycia informacji powiązanych zamiast wywoływania [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) dla każdego z przywoływanych importów. Jeśli sygnatura czasowa lub preferowany adres nie są zgodne z załadowanej biblioteki DLL, funkcja pomocnika przyjmuje, że powiązane IAT są nieaktualne i będą działać tak, jakby powiązane IAT nie istniały.

   NOBIND powoduje, że obraz programu jest większy, ale może skrócić czas ładowania biblioteki DLL. Jeśli nigdy nie zamierzasz powiązać biblioteki DLL, NOBIND uniemożliwi generowanie powiązanej IAT.

Aby określić biblioteki DLL do opóźnienia ładowania, użyj opcji [/DELAYLOAD](delayload-delay-load-import.md) .

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać więcej informacji, zobacz [ C++ Ustawianie kompilatora i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Rozwiń węzeł **Właściwości konfiguracji**, **konsolidator**, a następnie wybierz pozycję **Zaawansowane**.

1. Zmodyfikuj właściwość **dll** załadowanej z opóźnieniem.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
