---
title: Tworzenie aplikacji OpenGL ES w systemach Android i iOS
ms.date: 10/09/2019
ms.assetid: 76a67886-df57-4a81-accb-2e3c2eaf607b
ms.openlocfilehash: 23dd9dbb1ff32050494e0d1d105cd55de3123fbb
ms.sourcegitcommit: a673f6a54cc97e3d4cd032b10aa8dce7f0539d39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78177676"
---
# <a name="build-an-opengl-es-application-on-android-and-ios"></a>Tworzenie aplikacji OpenGL ES w systemach Android i iOS

Możesz tworzyć rozwiązania i projekty programu Visual Studio dla aplikacji systemu iOS i aplikacji systemu Android, które współużytkują wspólny kod. Ten artykuł przeprowadzi Cię przez połączony szablon rozwiązania. Tworzy zarówno aplikację systemu iOS, jak i natywną aplikację działania systemu Android. Aplikacje mają C++ wspólny kod, który używa technologii OpenGL ES do wyświetlania tego samego animowanego, obracanego modułu na każdej platformie. Oprogramowanie OpenGL ES (OpenGL dla systemów osadzonych lub GLES) jest interfejsem API grafiki 2D i 3D. Jest ona obsługiwana na wielu urządzeniach przenośnych.

## <a name="requirements"></a>Wymagania

Zapoznaj się ze wszystkimi wymaganiami systemowymi, aby utworzyć aplikację OpenGL ES dla systemów iOS i Android. Jeśli jeszcze tego nie zrobiono, zainstaluj Programowanie aplikacji C++ mobilnych przy użyciu obciążenia w Instalator programu Visual Studio. Aby uzyskać szablony OpenGL ES oraz do kompilowania dla systemu iOS, Dołącz opcjonalne C++ narzędzia programistyczne dla systemu iOS. Aby skompilować system Android, zainstaluj narzędzia C++ deweloperskie dla systemu Android i wymagane narzędzia innych firm: Android NDK, Apache Ant i Google emulator systemu Android.

W celu uzyskania lepszej wydajności emulatora na platformach firmy Intel jedną z opcji jest zainstalowanie Hardware Accelerated Execution Manager firmy Intel (HAXM). Aby uzyskać szczegółowe instrukcje, zobacz [Instalowanie aplikacji mobilnych dla wielu platform C++za pomocą programu ](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md).

Do kompilowania i testowania aplikacji dla systemu iOS potrzebny jest komputer Mac. Skonfiguruj je zgodnie z instrukcjami instalacji. Aby uzyskać więcej informacji na temat sposobu konfigurowania programu do tworzenia aplikacji dla systemu iOS, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilowania przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

## <a name="create-a-new-opengles-application-project"></a>Utwórz nowy projekt aplikacji OpenGL

W tym samouczku najpierw utworzysz nowy projekt aplikacji OpenGL ES. a następnie Skompiluj i uruchom aplikację domyślną w emulatorze systemu Android. Następnie utworzysz aplikację dla systemu iOS i uruchomisz aplikację na urządzeniu z systemem iOS.

::: moniker range="vs-2017"

1. W programie Visual Studio wybierz kolejno pozycje **plik** > **Nowy** > **projekt**.

1. W oknie dialogowym **Nowy projekt** w obszarze **Szablony**wybierz pozycję **Visual C++**  > **cross platform**, a następnie wybierz szablon **aplikacja opengls (Android, iOS)** .

1. Nadaj aplikacji nazwę, na przykład *MyOpenGLESApp*, a następnie wybierz przycisk **OK**.

   ![Nowy projekt aplikacji OpenGL](../cross-platform/media/cppmdd-opengles-newproj.png "Nowy projekt aplikacji OpenGL")

   Program Visual Studio tworzy nowe rozwiązanie i otwiera Eksplorator rozwiązań.

   ![MyOpenGLESApp w Eksplorator rozwiązań](../cross-platform/media/cppmdd-opengles-solexpl.png "MyOpenGLESApp w Eksplorator rozwiązań")

::: moniker-end

::: moniker range=">=vs-2019"

1. W programie Visual Studio wybierz kolejno pozycje **plik** > **Nowy** > **projekt**.

1. W oknie dialogowym **Utwórz nowy projekt** wybierz szablon **aplikacja opengls (Android, iOS)** , a następnie wybierz przycisk **dalej**.

1. W oknie dialogowym **Konfigurowanie nowego projektu** wprowadź nazwę, taką jak *MyOpenGLESApp* w polu **Nazwa projektu**, a następnie wybierz pozycję **Utwórz**.

   Program Visual Studio tworzy nowe rozwiązanie i otwiera Eksplorator rozwiązań.

   ![MyOpenGLESApp w Eksplorator rozwiązań](../cross-platform/media/cppmdd-opengles-solexpl.png "MyOpenGLESApp w Eksplorator rozwiązań")

::: moniker-end

Nowe rozwiązanie aplikacji OpenGL ES zawiera trzy projekty biblioteki i dwa projekty aplikacji. Folder biblioteki zawiera współużytkowany projekt kodu. I dwa projekty specyficzne dla platformy, które odwołują się do udostępnionego kodu:

- `MyOpenGLESApp.Android.NativeActivity` zawiera kod odwołania i Glue, który implementuje aplikację jako natywną aktywność w systemie Android. Punkty wejścia z kodu łączenia są zaimplementowane w *Main. cpp*, który obejmuje wspólny kod współużytkowany w `MyOpenGLESApp.Shared`. Wstępnie skompilowane nagłówki znajdują się w pliku *PCH. h*. Ten projekt aplikacji natywnej aktywności jest kompilowany do pliku biblioteki udostępnionej ( *. so*), który jest wybierany przez projekt `MyOpenGLESApp.Android.Packaging`.

- `MyOpenGLESApp.iOS.StaticLibrary` tworzy plik statycznej biblioteki systemu iOS ( *. a*), który zawiera kod współużytkowany w `MyOpenGLESApp.Shared`. Jest on połączony z aplikacją utworzoną przez projekt `MyOpenGLESApp.iOS.Application`.

- `MyOpenGLESApp.Shared` zawiera kod współużytkowany, który działa na różnych platformach. Używa makr preprocesora do kompilacji warunkowej kodu specyficznego dla platformy. Kod współużytkowany jest wybierany przez odwołanie do projektu w obu `MyOpenGLESApp.Android.NativeActivity` i `MyOpenGLESApp.iOS.StaticLibrary`.

Rozwiązanie ma dwa projekty do kompilowania aplikacji dla platform Android i iOS:

- `MyOpenGLESApp.Android.Packaging` tworzy plik *. apk* do wdrożenia na urządzeniu z systemem Android lub w emulatorze. Ten plik zawiera zasoby i plik pliku AndroidManifest. XML, w którym są ustawiane właściwości manifestu. Zawiera również plik *Build. XML* , który kontroluje proces kompilacji ANT. Domyślnie jest ustawiony jako projekt startowy, aby można go było wdrożyć i uruchomić bezpośrednio z programu Visual Studio.

- `MyOpenGLESApp.iOS.Application` zawierają zasoby i kod przyklejania do języka C, aby utworzyć aplikację dla systemu iOS, C++ która łączy się z kodem biblioteki statycznej w `MyOpenGLESApp.iOS.StaticLibrary`. Ten projekt tworzy pakiet kompilacji, który jest przesyłany do komputera Mac przez program Visual Studio i agenta zdalnego. Podczas kompilowania projektu program Visual Studio wysyła pliki i polecenia, aby kompilować i wdrażać aplikację na komputerze Mac.

## <a name="build-and-run-the-android-app"></a>Kompilowanie i uruchamianie aplikacji systemu Android

Rozwiązanie utworzone przez szablon ustawia aplikację dla systemu Android jako projekt domyślny.  Możesz skompilować i uruchomić tę aplikację, aby zweryfikować instalację i konfigurację. Aby sprawdzić początkowy test, uruchom aplikację na jednym z profili urządzeń zainstalowanych przez emulator dla systemu Android. Jeśli wolisz przetestować aplikację w innym miejscu docelowym, możesz załadować emulator docelowy. Lub podłącz urządzenie do komputera.

### <a name="to-build-and-run-the-android-native-activity-app"></a>Aby skompilować i uruchomić aplikację natywnego działania systemu Android

1. Jeśli nie została jeszcze wybrana, wybierz pozycję **x86** z listy rozwijanej **platformy rozwiązań** .

   ![Ustaw platformę rozwiązania na x86](../cross-platform/media/cppmdd-opengles-solutionplat.png "Ustaw platformę rozwiązania na x86")

   Użyj procesora x86, aby wskazać emulator. Aby wybrać urządzenie docelowe, Wybierz platformę rozwiązania opartą na procesorze urządzeń. Jeśli lista **platform rozwiązania** nie zostanie wyświetlona, wybierz pozycję **platformy rozwiązań** z listy **Dodaj/Usuń przyciski** , a następnie wybierz swoją platformę.

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla `MyOpenGLESApp.Android.Packaging` projektu, a następnie wybierz polecenie **Kompiluj**.

   ![Kompiluj projekt pakietu systemu Android](../cross-platform/media/cppmdd-opengles-andbuild.png "Kompiluj projekt pakietu systemu Android")

   W oknie danych wyjściowych zostaną wyświetlone dane wyjściowe procesu kompilacji dla biblioteki udostępnionej systemu Android i aplikacji systemu Android.

   ![Dane wyjściowe kompilacji dla projektów systemu Android](../cross-platform/media/cppmdd-opengles-andoutput.png "Dane wyjściowe kompilacji dla projektów systemu Android")

1. Wybierz jeden z emulowanych profilów urządzeń z systemem Android jako cel wdrożenia.

   ![Wybierz cel wdrożenia](../cross-platform/media/cppmdd-opengles-pickemulator.png "Wybierz cel wdrożenia")

   Być może zainstalowano Inne emulatory lub połączenie z urządzeniem z systemem Android. Można je wybrać z listy rozwijanej cel wdrożenia. Aby uruchomić aplikację, skompilowana platforma rozwiązania musi być zgodna z platformą urządzenia docelowego.

1. Naciśnij klawisz **F5** , aby rozpocząć debugowanie, lub **przesuń**+**F5** , aby rozpocząć bez debugowania.

   Program Visual Studio uruchamia emulator, który zajmuje kilka sekund, aby załadować i wdrożyć swój kod. Oto jak aplikacja jest wyświetlana w emulatorze:

   ![Aplikacja działająca w Emulator systemu Android](../cross-platform/media/cppmdd-opengles-andemulator.png "Aplikacja działająca w Emulator systemu Android")

   Po rozpoczęciu pracy aplikacji można ustawić punkty przerwania i użyć debugera do przechodzenia przez kod, badania wartości lokalnych i obserwacji.

1. Naciśnij klawisz **Shift**+**F5** , aby zatrzymać debugowanie.

   Emulator to oddzielny proces, który jest nadal uruchamiany. Można edytować, kompilować i wdrażać kod wielokrotnie w tym samym emulatorze. Aplikacja zostanie wyświetlona w kolekcji aplikacji na emulatorze i może być od razu uruchomiona.

   Wygenerowana aplikacja systemu Android Native Activity i projekty biblioteki umieszczają kod C++ współużytkowany w bibliotece dynamicznej. Zawiera kod "Glue" do interfejsu z platformą systemu Android. Większość kodu aplikacji znajduje się w bibliotece. Instrukcje manifestu, zasobów i kompilacji znajdują się w projekcie pakietu. Kod współużytkowany jest wywoływany z Main. cpp w projekcie natywnym. Aby uzyskać więcej informacji o tym, jak programować działanie systemu Android Native, zobacz stronę [pojęcia](https://developer.android.com/ndk/guides/concepts.html) dla deweloperów systemu Android.

   Visual Studio kompiluje natywne projekty aktywności systemu Android przy użyciu systemu Android NDK. Używa Clang jako zestawu narzędzi platformy. Program Visual Studio mapuje właściwości projektu do poleceń Kompiluj, Połącz i Debuguj na platformie docelowej. Aby uzyskać szczegółowe informacje, Otwórz okno dialogowe **strony właściwości** dla projektu MyOpenGLESApp. Android. Native. Aby uzyskać więcej informacji na temat przełączników wiersza polecenia, zobacz [Podręcznik użytkownika kompilatora Clang](http://clang.llvm.org/docs/UsersManual.html).

## <a name="build-and-run-the-ios-app-on-an-ios-device"></a>Kompilowanie i uruchamianie aplikacji dla systemu iOS na urządzeniu z systemem iOS

Tworzenie i edytowanie projektu aplikacji systemu iOS w programie Visual Studio. Ze względu na ograniczenia licencjonowania należy je skompilować i wdrożyć z poziomu komputera Mac. Program Visual Studio komunikuje się ze zdalnym agentem uruchomionym na komputerze Mac w celu transferu plików projektu oraz wykonywania poleceń kompilowania, wdrażania i debugowania. Skonfiguruj i skonfiguruj komputery Mac i Visual Studio, aby komunikować się przed rozpoczęciem tworzenia aplikacji dla systemu iOS. Aby uzyskać szczegółowe instrukcje, zobacz [Instalowanie i Konfigurowanie narzędzi do kompilowania przy użyciu systemu iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Uruchom agenta zdalnego na komputerze Mac i posparowanie go z programem Visual Studio. Następnie możesz skompilować i uruchomić aplikację systemu iOS, aby zweryfikować instalację i konfigurację.

Aby wdrożyć aplikację na urządzeniu z systemem iOS, najpierw Skonfiguruj automatyczne logowanie w usłudze Xcode. Automatyczne podpisywanie tworzy profil aprowizacji, aby podpisać kompilację aplikacji.

### <a name="to-set-up-automatic-signing-on-xcode"></a>Aby skonfigurować automatyczne podpisywanie na Xcode

1. Jeśli jeszcze tego nie zrobiono, zainstaluj program [Xcode](https://developer.apple.com/xcode/) na komputerze Mac.

1. Otwórz aplikację Xcode na komputerze Mac.

1. Utwórz nowy projekt **aplikacji pojedynczego widoku** Xcode. Wypełnij pola wymagane podczas tworzenia projektu. Wartości mogą być dowolne, ponieważ projekt jest używany tylko do tworzenia profilu aprowizacji, który jest używany później do podpisywania kompilacji aplikacji.

1. Dodaj identyfikator firmy Apple zarejestrowany na koncie [programu Apple Developer](https://developer.apple.com/programs/) , aby Xcode. Identyfikator Apple ID jest używany jako tożsamość podpisująca do podpisywania aplikacji. Aby dodać swoją tożsamość podpisującą w programie Xcode, otwórz menu **Xcode** i wybierz polecenie **Preferences (Preferencje**). Wybierz pozycję **konta** , a następnie kliknij przycisk Dodaj (+), aby dodać identyfikator Apple ID. Aby uzyskać szczegółowe instrukcje, zobacz [Dodawanie konta Apple ID](https://help.apple.com/xcode/mac/current/#/devaf282080a).

1. W ustawieniach "ogólne" projektu Xcode Zmień wartość **identyfikatora pakietu** na `com.<NameOfVSProject>`, gdzie `<NameOfVSProject>` jest taka sama jak nazwa projektu rozwiązania programu Visual Studio, który został utworzony. Na przykład jeśli utworzono projekt o nazwie `MyOpenGLESApp` w programie Visual Studio, ustaw **Identyfikator pakietu** na `com.MyOpenGLESApp`.

   ![Identyfikator pakietu Xcode](../cross-platform/media/cppmdd-opengles-iosxcodeid.png "Identyfikator pakietu Xcode")

1. Aby włączyć automatyczne podpisywanie, sprawdź. Automatyczne zarządzanie podpisywaniem * *.

   ![Xcode automatyczne podpisywanie](../cross-platform/media/cppmdd-opengles-iosxcodesign.png "Xcode automatyczne podpisywanie")

1. Wybierz nazwę zespołu identyfikatora Apple ID, który został dodany jako **zespół**programistyczny.

   ![Zespół Xcode](../cross-platform/media/cppmdd-opengles-iosxcodeteam.png "Zespół Xcode")

### <a name="to-build-and-run-the-ios-app-on-an-ios-device"></a>Aby skompilować i uruchomić aplikację systemu iOS na urządzeniu z systemem iOS

1. Uruchom agenta zdalnego na komputerze Mac i sprawdź, czy program Visual Studio jest sparowany z agentem zdalnym. Aby uruchomić agenta zdalnego, Otwórz okno aplikacji terminalowej i wprowadź `vcremote`. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zdalnego agenta w programie Visual Studio](../cross-platform/install-and-configure-tools-to-build-using-ios.md#ConfigureVS).

   ![Okno terminalu Mac z systemem vcremote](../cross-platform/media/cppmdd-common-vcremote.png "Okno terminalu Mac z systemem vcremote")

1. Dołącz urządzenie z systemem iOS do komputera Mac. Po dołączeniu urządzenia do komputera po raz pierwszy zostanie wyświetlony monit z pytaniem o to, czy komputer ma dostęp do urządzenia. Zezwól urządzeniu na ufanie komputerowi Mac.

1. W programie Visual Studio, jeśli nie jest jeszcze wybrana, Wybierz platformę rozwiązania z listy rozwijanej **platformy rozwiązania** na podstawie procesora urządzenia. W tym przykładzie jest to procesor **arm64** .

   ![Ustaw platformę rozwiązania na ARM64](../cross-platform/media/cppmdd-opengles-pickplatformarm64.png "Ustaw platformę rozwiązania na ARM64")

1. W Eksplorator rozwiązań otwórz menu skrótów dla projektu MyOpenGLESApp. iOS. Application i wybierz polecenie **Zwolnij projekt** , aby zwolnić projekt.

1. Ponownie otwórz menu skrótów dla niezaładowanego projektu MyOpenGLESApp. iOS. Application i wybierz polecenie **Edytuj projekt. PBXPROJ** , aby edytować plik projektu. W pliku `project.pbxproj` odszukaj atrybut `buildSettings` i Dodaj `DEVELOPMENT_TEAM` przy użyciu identyfikatora zespołu firmy Apple. Na poniższym zrzucie ekranu przedstawiono przykładową wartość `123456ABC` dla identyfikatora zespołu firmy Apple. Wartość identyfikatora zespołu firmy Apple można znaleźć z Xcode. Przejdź do pozycji **Ustawienia kompilacji** i umieść kursor nad nazwą zespołu deweloperów, aby wyświetlić etykietkę narzędzia. W etykietce narzędzia zostanie wyświetlony identyfikator Twojego zespołu.

   ![Ustaw zespół programistyczny](../cross-platform/media/cppmdd-opengles-iosdevelopmentteam.png "Ustaw zespół programistyczny")

1. Zamknij plik `project.pbxproj`, a następnie otwórz menu skrótów dla projektu niezaładowane MyOpenGLESApp. iOS. Application i wybierz polecenie **Załaduj ponownie projekt** , aby ponownie załadować projekt.

1. Teraz Skompiluj projekt MyOpenGLESApp. iOS. Application, otwierając menu skrótów dla projektu i wybierając opcję **Kompiluj**.

   ![Kompiluj projekt aplikacji systemu iOS](../cross-platform/media/cppmdd-opengles-iosbuild.png "Kompiluj projekt aplikacji systemu iOS")

   W oknie danych wyjściowych zostaną wyświetlone dane wyjściowe procesu kompilacji. Przedstawia wyniki dla biblioteki statycznej systemu iOS i aplikacji systemu iOS. Na komputerze Mac okno terminalu z uruchomionym agentem zdalnym pokazuje działanie polecenia i transferu plików.

   Na komputerze Mac może zostać wyświetlony monit o umożliwienie współprojektowania dostępu do łańcucha kluczy. Wybierz pozycję **Zezwól** , aby kontynuować.

1. Wybierz urządzenie z systemem iOS na pasku narzędzi, aby uruchomić aplikację na urządzeniu podłączonym do komputera Mac. Jeśli aplikacja nie zostanie uruchomiona, sprawdź, czy urządzenie udziela użytkownikowi uprawnień do wykonywania wdrożonej aplikacji na urządzeniu. To uprawnienie można ustawić, przechodząc do **ustawień** > **Ogólne** > **Zarządzanie urządzeniami** na urządzeniu. Wybierz swoje konto aplikacji dla deweloperów, Zaufaj swojemu kontu i Sprawdź aplikację. Spróbuj ponownie uruchomić aplikację z programu Visual Studio.

   ![Aplikacja systemu iOS na urządzeniu z systemem iOS](../cross-platform/media/cppmdd-opengles-iosdevice.png "Aplikacja systemu iOS na urządzeniu z systemem iOS")

   Po rozpoczęciu pracy aplikacji można ustawić punkty przerwania i użyć debugera programu Visual Studio, aby sprawdzić ustawienia regionalne, zobaczyć stos wywołań i obserwować wartości.

   ![Debuger w aplikacji systemu iOS](../cross-platform/media/cppmdd-opengles-iosdebug.png "Debuger w aplikacji systemu iOS")

1. Naciśnij klawisz **Shift**+**F5** , aby zatrzymać debugowanie.

   Wygenerowane projekty aplikacji i biblioteki systemu iOS umieszczają C++ kod w bibliotece statycznej, która implementuje tylko kod współużytkowany. Większość kodu aplikacji znajduje się w projekcie `Application`. Wywołania kodu biblioteki udostępnionej w tym projekcie szablonu są wykonywane w pliku *GameViewController. m* . Aby skompilować aplikację dla systemu iOS, program Visual Studio używa zestawu narzędzi platformy Xcode, który wymaga komunikacji z klientem zdalnym działającym na komputerze Mac.

   Program Visual Studio transferuje pliki projektu do zdalnego klienta. Następnie wysyła polecenia do kompilowania aplikacji przy użyciu Xcode. Klient zdalny wysyła informacje o stanie kompilacji z powrotem do programu Visual Studio. Po pomyślnym skompilowaniu aplikacji program Visual Studio może wysyłać polecenia do uruchamiania i debugowania aplikacji. Debuger w programie Visual Studio kontroluje aplikację uruchomioną na urządzeniu z systemem iOS podłączonym do komputera Mac. Program Visual Studio mapuje właściwości projektu do opcji używanych do kompilowania, łączenia i debugowania na docelowej platformie systemu iOS. Aby uzyskać szczegółowe informacje na temat opcji wiersza polecenia kompilatora, Otwórz okno dialogowe **strony właściwości** dla projektu MyOpenGLESApp. iOS. StaticLibrary.

## <a name="customize-your-apps"></a>Dostosowywanie aplikacji

Możesz zmodyfikować kod współużytkowany C++ , aby dodać lub zmienić typowe funkcje. Zmień wywołania kodu udostępnionego w `MyOpenGLESApp.Android.NativeActivity` i `MyOpenGLESApp.iOS.Application` projekty do dopasowania. Można użyć makr preprocesora, aby określić sekcje specyficzne dla platformy w danym wspólnym kodzie. `__ANDROID__` makro preprocesora jest wstępnie zdefiniowane podczas kompilowania dla systemu Android. `__APPLE__` makro preprocesora jest wstępnie zdefiniowane podczas kompilowania dla systemu iOS.

Aby wyświetlić funkcję IntelliSense dla konkretnej platformy projektu, wybierz projekt na liście rozwijanej przełącznik kontekstu. Znajduje się na pasku nawigacyjnym u góry okna edytora.

![Lista rozwijana z przełącznikiem kontekstu projektu w edytorze](../cross-platform/media/cppmdd-opengles-contextswitcher.png)

Problemy z technologią IntelliSense w kodzie, który jest używany przez bieżący projekt, są oznaczone czerwoną linią falistą. Purpurowy znak falisty podkreśla problem w innych projektach. Program Visual Studio nie obsługuje kolorowania kodu ani funkcji IntelliSense dla plików Java lub języków języka C. Jednak nadal można modyfikować pliki źródłowe i zasoby. Użyj ich, aby ustawić nazwę aplikacji, ikonę i inne szczegóły implementacji.
