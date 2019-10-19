---
title: Klasa CPathT
ms.date: 03/27/2019
f1_keywords:
- CPathT
- ATLPATH/ATL::CPathT
- ATLPATH/ATL::CPathT::PCXSTR
- ATLPATH/ATL::CPathT::PXSTR
- ATLPATH/ATL::CPathT::XCHAR
- ATLPATH/ATL::CPathT::CPathT
- ATLPATH/ATL::CPathT::AddBackslash
- ATLPATH/ATL::CPathT::AddExtension
- ATLPATH/ATL::CPathT::Append
- ATLPATH/ATL::CPathT::BuildRoot
- ATLPATH/ATL::CPathT::Canonicalize
- ATLPATH/ATL::CPathT::Combine
- ATLPATH/ATL::CPathT::CommonPrefix
- ATLPATH/ATL::CPathT::CompactPath
- ATLPATH/ATL::CPathT::CompactPathEx
- ATLPATH/ATL::CPathT::FileExists
- ATLPATH/ATL::CPathT::FindExtension
- ATLPATH/ATL::CPathT::FindFileName
- ATLPATH/ATL::CPathT::GetDriveNumber
- ATLPATH/ATL::CPathT::GetExtension
- ATLPATH/ATL::CPathT::IsDirectory
- ATLPATH/ATL::CPathT::IsFileSpec
- ATLPATH/ATL::CPathT::IsPrefix
- ATLPATH/ATL::CPathT::IsRelative
- ATLPATH/ATL::CPathT::IsRoot
- ATLPATH/ATL::CPathT::IsSameRoot
- ATLPATH/ATL::CPathT::IsUNC
- ATLPATH/ATL::CPathT::IsUNCServer
- ATLPATH/ATL::CPathT::IsUNCServerShare
- ATLPATH/ATL::CPathT::MakePretty
- ATLPATH/ATL::CPathT::MatchSpec
- ATLPATH/ATL::CPathT::QuoteSpaces
- ATLPATH/ATL::CPathT::RelativePathTo
- ATLPATH/ATL::CPathT::RemoveArgs
- ATLPATH/ATL::CPathT::RemoveBackslash
- ATLPATH/ATL::CPathT::RemoveBlanks
- ATLPATH/ATL::CPathT::RemoveExtension
- ATLPATH/ATL::CPathT::RemoveFileSpec
- ATLPATH/ATL::CPathT::RenameExtension
- ATLPATH/ATL::CPathT::SkipRoot
- ATLPATH/ATL::CPathT::StripPath
- ATLPATH/ATL::CPathT::StripToRoot
- ATLPATH/ATL::CPathT::UnquoteSpaces
- ATLPATH/ATL::CPathT::m_strPath
helpviewer_keywords:
- CPathT class
ms.assetid: eba4137d-1fd2-4b44-a2e1-0944db64df3c
ms.openlocfilehash: ba1c831d772deef34449d17adc2c8e7a6f90eaef
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "69496615"
---
# <a name="cpatht-class"></a>Klasa CPathT

Ta klasa reprezentuje ścieżkę.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
template <typename StringType>
class CPathT
```

#### <a name="parameters"></a>Parametry

*StringType*<br/>
Klasa ATL/MFC do użycia dla ścieżki (zobacz [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)).

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|[CPathT::P CXSTR](#pcxstr)|Typ stałej ciągu.|
|[CPathT::P XSTR](#pxstr)|Typ ciągu.|
|[CPathT::XCHAR](#xchar)|Typ znaku.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPathT::CPathT](#cpatht)|Konstruktor dla ścieżki.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPathT::AddBackslash](#addbackslash)|Wywołaj tę metodę, aby dodać ukośnik odwrotny do końca ciągu, aby utworzyć poprawną składnię dla ścieżki.|
|[CPathT:: AddExtension](#addextension)|Wywołaj tę metodę, aby dodać rozszerzenie pliku do ścieżki.|
|[CPathT:: Append](#append)|Wywołaj tę metodę, aby dołączyć ciąg do bieżącej ścieżki.|
|[CPathT:: element buildroot](#buildroot)|Wywołaj tę metodę, aby utworzyć ścieżkę główną z danego numeru dysku.|
|[CPathT:: sprowadź](#canonicalize)|Wywołaj tę metodę, aby skonwertować ścieżkę do formy kanonicznej.|
|[CPathT:: Połącz](#combine)|Wywołaj tę metodę, aby połączyć ciąg reprezentujący nazwę katalogu i ciąg reprezentujący nazwę ścieżki pliku do jednej ścieżki.|
|[CPathT::CommonPrefix](#commonprefix)|Wywołaj tę metodę, aby określić, czy określona ścieżka udostępnia wspólny prefiks z bieżącą ścieżką.|
|[CPathT::CompactPath](#compactpath)|Wywołaj tę metodę, aby obciąć ścieżkę pliku tak, aby mieściła się w danej szerokości pikseli przez zastępowanie składników ścieżki wielokropkiem.|
|[CPathT::CompactPathEx](#compactpathex)|Wywołaj tę metodę, aby obciąć ścieżkę pliku do rozmiaru w danej liczbie znaków, zastępując składniki ścieżki wielokropkiem.|
|[CPathT::FileExists](#fileexists)|Wywołaj tę metodę, aby sprawdzić, czy plik o tej nazwie ścieżki istnieje.|
|[CPathT::FindExtension](#findextension)|Wywołaj tę metodę, aby znaleźć pozycję rozszerzenia pliku w ścieżce.|
|[CPathT::FindFileName](#findfilename)|Wywołaj tę metodę, aby znaleźć pozycję nazwy pliku w ścieżce.|
|[CPathT::GetDriveNumber](#getdrivenumber)|Wywołaj tę metodę, aby wyszukać ścieżkę litery dysku w zakresie od "A" do "Z" i zwrócić odpowiedni numer dysku.|
|[CPathT:: GetExtension](#getextension)|Wywołaj tę metodę, aby uzyskać rozszerzenie pliku ze ścieżki.|
|[CPathT:: IsDirectory](#isdirectory)|Wywołaj tę metodę, aby sprawdzić, czy ścieżka jest prawidłowym katalogiem.|
|[CPathT::IsFileSpec](#isfilespec)|Wywołaj tę metodę, aby przeszukać ścieżkę do dowolnej ścieżki, ograniczając znaki (na przykład ":" lub "\\"). Jeśli nie ma żadnych znaków ograniczających ścieżki, ścieżka jest traktowana jako ścieżka do pliku specyfikacji.|
|[CPathT:: IsPrefix](#isprefix)|Wywołaj tę metodę, aby określić, czy ścieżka zawiera prawidłowy prefiks typu przekazaną przez *pszPrefix*.|
|[CPathT:: isrelatywn](#isrelative)|Wywołaj tę metodę, aby określić, czy ścieżka jest względna.|
|[CPathT:: IsRoot](#isroot)|Wywołaj tę metodę, aby określić, czy ścieżka jest katalogiem głównym katalogu.|
|[CPathT::IsSameRoot](#issameroot)|Wywołaj tę metodę, aby określić, czy inna ścieżka ma wspólny składnik główny z bieżącą ścieżką.|
|[CPathT::IsUNC](#isunc)|Wywołaj tę metodę, aby określić, czy ścieżka jest prawidłową ścieżką UNC (uniwersalną konwencją nazewnictwa) dla serwera i udziału.|
|[CPathT::IsUNCServer](#isuncserver)|Wywołaj tę metodę, aby określić, czy ścieżka jest prawidłową ścieżką UNC (uniwersalną konwencją nazewnictwa) tylko dla serwera.|
|[CPathT::IsUNCServerShare](#isuncservershare)|Wywołaj tę metodę, aby określić, czy ścieżka jest prawidłową ścieżką UNC (uniwersalną konwencją nazewnictwa), \\ \ *serwera* \ *udziału*.|
|[CPathT::MakePretty](#makepretty)|Wywołaj tę metodę, aby skonwertować ścieżkę do wszystkich małych liter, aby nadać ścieżce spójny wygląd.|
|[CPathT::MatchSpec](#matchspec)|Wywołaj tę metodę, aby wyszukać ciąg zawierający typ dopasowania z symbolami wieloznacznymi.|
|[CPathT::QuoteSpaces](#quotespaces)|Wywołaj tę metodę, aby umieścić ścieżkę w cudzysłowie, jeśli zawiera spacje.|
|[CPathT::RelativePathTo](#relativepathto)|Wywołaj tę metodę, aby utworzyć ścieżkę względną z jednego pliku lub folderu do innego.|
|[CPathT::RemoveArgs](#removeargs)|Wywołaj tę metodę, aby usunąć z ścieżki wszystkie argumenty wiersza polecenia.|
|[CPathT::RemoveBackslash](#removebackslash)|Wywołaj tę metodę, aby usunąć ukośnik odwrotny ze ścieżki.|
|[CPathT::RemoveBlanks](#removeblanks)|Wywołaj tę metodę, aby usunąć wszystkie spacje wiodące i końcowe ze ścieżki.|
|[CPathT::RemoveExtension](#removeextension)|Wywołaj tę metodę, aby usunąć rozszerzenie pliku ze ścieżki, jeśli istnieje.|
|[CPathT::RemoveFileSpec](#removefilespec)|Wywołaj tę metodę, aby usunąć końcową nazwę pliku i ukośnik odwrotny ze ścieżki, jeśli je zawiera.|
|[CPathT::RenameExtension](#renameextension)|Wywołaj tę metodę, aby zastąpić rozszerzenie nazwy pliku w ścieżce nowym rozszerzeniem. Jeśli nazwa pliku nie zawiera rozszerzenia, rozszerzenie zostanie dołączone do końca ciągu.|
|[CPathT::SkipRoot](#skiproot)|Wywołaj tę metodę, aby przeanalizować ścieżkę, ignorując litery dysku lub serwer UNC/udział części ścieżki.|
|[CPathT::StripPath](#strippath)|Wywołaj tę metodę, aby usunąć część w pełni kwalifikowanej ścieżki i nazwy pliku.|
|[CPathT::StripToRoot](#striptoroot)|Wywołaj tę metodę, aby usunąć wszystkie części ścieżki z wyjątkiem informacji głównych.|
|[CPathT::UnquoteSpaces](#unquotespaces)|Wywołaj tę metodę, aby usunąć znaki cudzysłowu z początku i końca ścieżki.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPathT:: operator const StringType &](#operator_const_stringtype_amp)|Ten operator pozwala, aby obiekt był traktowany jak ciąg.|
|[CPathT:: operator CPathT::P CXSTR](#operator_cpatht__pcxstr)|Ten operator pozwala, aby obiekt był traktowany jak ciąg.|
|[CPathT:: operator StringType &](#operator_stringtype_amp)|Ten operator pozwala, aby obiekt był traktowany jak ciąg.|
|[CPathT:: operator + =](#operator_add_eq)|Ten operator dołącza ciąg do ścieżki.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPathT::m_strPath](#m_strpath)|Ścieżka.|

## <a name="remarks"></a>Uwagi

`CPath`, `CPathA` i `CPathW` są wystąpieniami `CPathT` zdefiniowane w następujący sposób:

`typedef CPathT< CString > CPath;`

`typedef CPathT< CStringA > CPathA;`

`typedef CPathT< CStringW > CPathW;`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlpath. h

##  <a name="addbackslash"></a>CPathT::AddBackslash

Wywołaj tę metodę, aby dodać ukośnik odwrotny do końca ciągu, aby utworzyć poprawną składnię dla ścieżki. Jeśli ścieżka ma już końcowy ukośnik, nie zostanie dodany ukośnik odwrotny.

```
void AddBackslash();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathAddBackSlash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw).

##  <a name="addextension"></a>CPathT:: AddExtension

Wywołaj tę metodę, aby dodać rozszerzenie pliku do ścieżki.

```
BOOL AddExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>Parametry

*pszExtension*<br/>
Rozszerzenie pliku do dodania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw).

##  <a name="append"></a>CPathT:: Append

Wywołaj tę metodę, aby dołączyć ciąg do bieżącej ścieżki.

```
BOOL Append(PCXSTR pszMore);
```

### <a name="parameters"></a>Parametry

*pszMore*<br/>
Ciąg do dołączenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw).

##  <a name="buildroot"></a>CPathT:: element buildroot

Wywołaj tę metodę, aby utworzyć ścieżkę główną z danego numeru dysku.

```
void BuildRoot(int iDrive);
```

### <a name="parameters"></a>Parametry

*iDrive*<br/>
Numer stacji (0 to:, 1 to B: itd.).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw).

##  <a name="canonicalize"></a>CPathT:: sprowadź

Wywołaj tę metodę, aby skonwertować ścieżkę do formy kanonicznej.

```
void Canonicalize();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew).

##  <a name="combine"></a>CPathT:: Połącz

Wywołaj tę metodę, aby połączyć ciąg reprezentujący nazwę katalogu i ciąg reprezentujący nazwę ścieżki pliku do jednej ścieżki.

```
void Combine(PCXSTR pszDir, PCXSTR  pszFile);
```

### <a name="parameters"></a>Parametry

*pszDir*<br/>
Ścieżka katalogu.

*pszFile*<br/>
Ścieżka pliku.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew).

##  <a name="commonprefix"></a>CPathT::CommonPrefix

Wywołaj tę metodę, aby określić, czy określona ścieżka udostępnia wspólny prefiks z bieżącą ścieżką.

```
CPathT<StringType> CommonPrefix(PCXSTR pszOther);
```

### <a name="parameters"></a>Parametry

*pszOther*<br/>
Ścieżka do porównania z bieżącą.

### <a name="return-value"></a>Wartość zwracana

Zwraca wspólny prefiks.

### <a name="remarks"></a>Uwagi

Prefiks jest jednym z następujących typów: "C: \\ \\", ".", "..", ".. \\ \\ ". Aby uzyskać więcej informacji, zobacz [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw).

##  <a name="compactpath"></a>CPathT::CompactPath

Wywołaj tę metodę, aby obciąć ścieżkę pliku tak, aby mieściła się w danej szerokości pikseli przez zastępowanie składników ścieżki wielokropkiem.

```
BOOL CompactPath(HDC hDC, UINT nWidth);
```

### <a name="parameters"></a>Parametry

*Używający HDC*<br/>
Kontekst urządzenia używany do metryk czcionki.

*nWidth*<br/>
Szerokość (w pikselach), do której zostanie wymuszone dopasowanie ciągu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw).

##  <a name="compactpathex"></a>CPathT::CompactPathEx

Wywołaj tę metodę, aby obciąć ścieżkę pliku do rozmiaru w danej liczbie znaków, zastępując składniki ścieżki wielokropkiem.

```
BOOL CompactPathEx(UINT nMaxChars, DWORD dwFlags = 0);
```

### <a name="parameters"></a>Parametry

*nMaxChars*<br/>
Maksymalna liczba znaków, które mają być zawarte w nowym ciągu, łącznie z kończącym znakiem NULL.

*flagiDW*<br/>
Rezerwacj.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw).

##  <a name="cpatht"></a>CPathT::CPathT

Konstruktor.

```
CPathT(PCXSTR pszPath);
CPathT(const CPathT<StringType>& path);
CPathT() throw();
```

### <a name="parameters"></a>Parametry

*pszPath*<br/>
Wskaźnik do ciągu ścieżki.

*ścieżka*<br/>
Ciąg ścieżki.

##  <a name="fileexists"></a>CPathT::FileExists

Wywołaj tę metodę, aby sprawdzić, czy plik o tej nazwie ścieżki istnieje.

```
BOOL FileExists() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli plik istnieje, w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw).

##  <a name="findextension"></a>CPathT::FindExtension

Wywołaj tę metodę, aby znaleźć pozycję rozszerzenia pliku w ścieżce.

```
int FindExtension() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca pozycję "." poprzedzającą rozszerzenie. Jeśli rozszerzenie nie zostanie znalezione, zwraca wartość-1.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw).

##  <a name="findfilename"></a>CPathT::FindFileName

Wywołaj tę metodę, aby znaleźć pozycję nazwy pliku w ścieżce.

```
int FindFileName() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca pozycję nazwy pliku. Jeśli nazwa pliku nie zostanie znaleziona, zwraca wartość-1.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew).

##  <a name="getdrivenumber"></a>CPathT::GetDriveNumber

Wywołaj tę metodę, aby wyszukać ścieżkę litery dysku w zakresie od "A" do "Z" i zwrócić odpowiedni numer dysku.

```
int GetDriveNumber() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca numer stacji jako liczbę całkowitą z przedziału od 0 do 25 (odpowiadającą od "A" do "Z"), jeśli ścieżka ma literę dysku lub-1 w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw).

##  <a name="getextension"></a>CPathT:: GetExtension

Wywołaj tę metodę, aby uzyskać rozszerzenie pliku ze ścieżki.

```
StringType GetExtension() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca rozszerzenie pliku.

##  <a name="isdirectory"></a>CPathT:: IsDirectory

Wywołaj tę metodę, aby sprawdzić, czy ścieżka jest prawidłowym katalogiem.

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość różną od zera (16), jeśli ścieżka jest katalogiem, w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw).

##  <a name="isfilespec"></a>CPathT::IsFileSpec

Wywołaj tę metodę, aby przeszukać ścieżkę do dowolnej ścieżki, ograniczając znaki (na przykład ":" lub "\\"). Jeśli nie ma żadnych znaków ograniczających ścieżki, ścieżka jest traktowana jako ścieżka do pliku specyfikacji.

```
BOOL IsFileSpec() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli w ścieżce nie ma znaków ograniczających ścieżkę lub wartość FAŁSZ, jeśli istnieją znaki ograniczające ścieżkę.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw).

##  <a name="isprefix"></a>CPathT:: IsPrefix

Wywołaj tę metodę, aby określić, czy ścieżka zawiera prawidłowy prefiks typu przekazaną przez *pszPrefix*.

```
BOOL IsPrefix(PCXSTR pszPrefix) const;
```

### <a name="parameters"></a>Parametry

*pszPrefix*<br/>
Prefiks do wyszukania. Prefiks jest jednym z następujących typów: "C: \\ \\", ".", "..", ".. \\ \\ ".

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli ścieżka zawiera prefiks lub wartość FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw).

##  <a name="isrelative"></a>CPathT:: isrelatywn

Wywołaj tę metodę, aby określić, czy ścieżka jest względna.

```
BOOL IsRelative() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli ścieżka jest względna, lub FALSE, jeśli jest bezwzględna.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew).

##  <a name="isroot"></a>CPathT:: IsRoot

Wywołaj tę metodę, aby określić, czy ścieżka jest katalogiem głównym katalogu.

```
BOOL IsRoot() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli ścieżka jest katalogiem głównym lub w przeciwnym razie ma wartość FALSE.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw).

##  <a name="issameroot"></a>CPathT::IsSameRoot

Wywołaj tę metodę, aby określić, czy inna ścieżka ma wspólny składnik główny z bieżącą ścieżką.

```
BOOL IsSameRoot(PCXSTR pszOther) const;
```

### <a name="parameters"></a>Parametry

*pszOther*<br/>
Druga ścieżka.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli oba ciągi mają ten sam główny składnik lub w przeciwnym razie zwraca wartość FALSE.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw).

##  <a name="isunc"></a>CPathT::IsUNC

Wywołaj tę metodę, aby określić, czy ścieżka jest prawidłową ścieżką UNC (uniwersalną konwencją nazewnictwa) dla serwera i udziału.

```
BOOL IsUNC() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli ścieżka jest prawidłową ścieżką UNC, lub FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw).

##  <a name="isuncserver"></a>CPathT::IsUNCServer

Wywołaj tę metodę, aby określić, czy ścieżka jest prawidłową ścieżką UNC (uniwersalną konwencją nazewnictwa) tylko dla serwera.

```
BOOL IsUNCServer() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli ciąg jest prawidłową ścieżką UNC tylko dla serwera (bez nazwy udziału) lub w przeciwnym razie zwraca wartość FALSE.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw).

##  <a name="isuncservershare"></a>CPathT::IsUNCServerShare

Wywołaj tę metodę, aby określić, czy ścieżka jest prawidłową ścieżką UNC (uniwersalną konwencją nazewnictwa), \\ \ *serwera* \ *udziału*.

```
BOOL IsUNCServerShare() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli ścieżka ma postać \\ \ *server* \ *Share*lub false w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).

##  <a name="m_strpath"></a>CPathT::m_strPath

Ścieżka.

```
StringType m_strPath;
```

### <a name="remarks"></a>Uwagi

`StringType` jest parametrem szablonu do `CPathT`.

##  <a name="makepretty"></a>CPathT::MakePretty

Wywołaj tę metodę, aby skonwertować ścieżkę do wszystkich małych liter, aby nadać ścieżce spójny wygląd.

```
BOOL MakePretty();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli ścieżka została przekonwertowana lub w przeciwnym razie ma wartość FALSE.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).

##  <a name="matchspec"></a>CPathT::MatchSpec

Wywołaj tę metodę, aby wyszukać ciąg zawierający typ dopasowania z symbolami wieloznacznymi.

```
BOOL MatchSpec(PCXSTR pszSpec) const;
```

### <a name="parameters"></a>Parametry

*pszSpec*<br/>
Wskaźnik na ciąg zakończony znakiem null z typem pliku do wyszukania. Na przykład, aby sprawdzić, czy plik w bieżącej ścieżce jest plikiem DOC, *pszSpec* powinien mieć wartość "*. doc".

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli ciąg pasuje lub ma wartość FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).

##  <a name="operator_add_eq"></a>CPathT:: operator + =

Ten operator dołącza ciąg do ścieżki.

```
CPathT<StringType>& operator+=(PCXSTR pszMore);
```

### <a name="parameters"></a>Parametry

*pszMore*<br/>
Ciąg do dołączenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca zaktualizowaną ścieżkę.

##  <a name="operator_const_stringtype_amp"></a>CPathT:: operator const StringType &amp;

Ten operator pozwala, aby obiekt był traktowany jak ciąg.

```
operator const StringType&() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ciąg reprezentujący bieżącą ścieżkę zarządzaną przez ten obiekt.

##  <a name="operator_cpatht__pcxstr"></a>CPathT:: operator CPathT::P CXSTR

Ten operator pozwala, aby obiekt był traktowany jak ciąg.

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ciąg reprezentujący bieżącą ścieżkę zarządzaną przez ten obiekt.

##  <a name="operator_stringtype_amp"></a>CPathT:: operator StringType &amp;

Ten operator pozwala, aby obiekt był traktowany jak ciąg.

```
operator StringType&() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ciąg reprezentujący bieżącą ścieżkę zarządzaną przez ten obiekt.

##  <a name="pcxstr"></a>CPathT::P CXSTR

Typ stałej ciągu.

```
typedef StringType::PCXSTR PCXSTR;
```

### <a name="remarks"></a>Uwagi

`StringType` jest parametrem szablonu do `CPathT`.

##  <a name="pxstr"></a>CPathT::P XSTR

Typ ciągu.

```
typedef StringType::PXSTR PXSTR;
```

### <a name="remarks"></a>Uwagi

`StringType` jest parametrem szablonu do `CPathT`.

##  <a name="quotespaces"></a>CPathT::QuoteSpaces

Wywołaj tę metodę, aby umieścić ścieżkę w cudzysłowie, jeśli zawiera spacje.

```
void QuoteSpaces();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).

##  <a name="relativepathto"></a>CPathT::RelativePathTo

Wywołaj tę metodę, aby utworzyć ścieżkę względną z jednego pliku lub folderu do innego.

```
BOOL RelativePathTo(
    PCXSTR pszFrom,
    DWORD dwAttrFrom,
    PCXSTR pszTo,
    DWORD dwAttrTo);
```

### <a name="parameters"></a>Parametry

*pszFrom*<br/>
Początek ścieżki względnej.

*dwAttrFrom*<br/>
Atrybuty pliku *pszFrom*. Jeśli ta wartość zawiera FILE_ATTRIBUTE_DIRECTORY, zakłada się, że *pszFrom* jest katalogiem. w przeciwnym razie przyjmuje się, że *pszFrom* jest plikiem.

*pszTo*<br/>
Punkt końcowy ścieżki względnej.

*dwAttrTo*<br/>
Atrybuty pliku *pszTo*. Jeśli ta wartość zawiera FILE_ATTRIBUTE_DIRECTORY, zakłada się, że *pszTo* jest katalogiem. w przeciwnym razie przyjmuje się, że *pszTo* jest plikiem.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).

##  <a name="removeargs"></a>CPathT::RemoveArgs

Wywołaj tę metodę, aby usunąć z ścieżki wszystkie argumenty wiersza polecenia.

```
void RemoveArgs();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).

##  <a name="removebackslash"></a>CPathT::RemoveBackslash

Wywołaj tę metodę, aby usunąć ukośnik odwrotny ze ścieżki.

```
void RemoveBackslash();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).

##  <a name="removeblanks"></a>CPathT::RemoveBlanks

Wywołaj tę metodę, aby usunąć wszystkie spacje wiodące i końcowe ze ścieżki.

```
void RemoveBlanks();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).

##  <a name="removeextension"></a>CPathT::RemoveExtension

Wywołaj tę metodę, aby usunąć rozszerzenie pliku ze ścieżki, jeśli istnieje.

```
void RemoveExtension();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).

##  <a name="removefilespec"></a>CPathT::RemoveFileSpec

Wywołaj tę metodę, aby usunąć końcową nazwę pliku i ukośnik odwrotny ze ścieżki, jeśli je zawiera.

```
BOOL RemoveFileSpec();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).

##  <a name="renameextension"></a>CPathT::RenameExtension

Wywołaj tę metodę, aby zastąpić rozszerzenie nazwy pliku w ścieżce nowym rozszerzeniem. Jeśli nazwa pliku nie zawiera rozszerzenia, rozszerzenie zostanie dołączone do końca ścieżki.

```
BOOL RenameExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>Parametry

*pszExtension*<br/>
Nowe rozszerzenie nazwy pliku poprzedzone znakiem ".".

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE dla sukcesu, FALSE w przypadku błędu.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).

##  <a name="skiproot"></a>CPathT::SkipRoot

Wywołaj tę metodę, aby przeanalizować ścieżkę, ignorując części dysku lub ścieżki UNC (Universal Naming Convention).

```
int SkipRoot() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca pozycję początku ścieżki podrzędnej, która następuje po elemencie głównym (litera dysku lub serwer/udział UNC).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).

##  <a name="strippath"></a>CPathT::StripPath

Wywołaj tę metodę, aby usunąć część w pełni kwalifikowanej ścieżki i nazwy pliku.

```
void StripPath();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).

##  <a name="striptoroot"></a>CPathT::StripToRoot

Wywołaj tę metodę, aby usunąć wszystkie części ścieżki z wyjątkiem informacji głównych.

```
BOOL StripToRoot();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli w ścieżce znaleziono prawidłową literę dysku lub w przeciwnym razie ma wartość FALSE.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).

##  <a name="unquotespaces"></a>CPathT::UnquoteSpaces

Wywołaj tę metodę, aby usunąć znaki cudzysłowu z początku i końca ścieżki.

```
void UnquoteSpaces();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).

##  <a name="xchar"></a>CPathT::XCHAR

Typ znaku.

```
typedef StringType::XCHAR XCHAR;
```

### <a name="remarks"></a>Uwagi

`StringType` jest parametrem szablonu do `CPathT`.

## <a name="see-also"></a>Zobacz także

[Klasy](../../atl/reference/atl-classes.md)<br/>
[CStringT, klasa](../../atl-mfc-shared/reference/cstringt-class.md)
