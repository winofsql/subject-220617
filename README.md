# subject-220617

![image](https://user-images.githubusercontent.com/1501327/174046686-ec516c54-ae66-4079-9f15-b22361a317e6.png)

```vbscript
<SCRIPT language="VBScript">
Dim objShell : Set objShell = CreateObject("Shell.Application")
Dim objFolder : Set objFolder = objShell.NameSpace(0)
</SCRIPT>
<html>
<head>
<title>Shell で開く Windows ツール</title>
<meta http-equiv="content-type" content="text/html; charset=SHIFT_JIS">
<HTA:APPLICATION ID="Sqlwin"
	BORDERSTYLE="sunken"
	INNERBORDER="yes"
	SCROLL="no"
	ICON="http://winofsql.jp/WinOfSql.ico"
>

<style type="text/css">
* {
	font-size:26px;
	font-family: "メイリオ", Meiryo, "ＭＳ Ｐゴシック", sans-serif;
}
</style>

<SCRIPT language=VBScript>
Function OpenDesktopFile( strTarget )

	Dim objFile

	Set objFile = objFolder.ParseName(strTarget)
	Call objFile.InvokeVerb()

End Function
Function OpenProp( strTarget )

	Dim objFile

	Set objFile = objFolder.ParseName(strTarget)
	objFile.InvokeVerb("properties")

End Function
Function ControlItemb( strName, strTarget )

	Dim ControlPanel,objFolder,objFolderItems

	ControlPanel = "::{26EE0668-A00A-44D7-9371-BEB064C98683}"
	Set objFolder = objShell.NameSpace(ControlPanel)

	Set objFolderItems = objFolder.Items
	For I = 0 to objFolderItems.Count - 1
		if objFolderItems.item(I).Name = strName then
			For J = 0 to objFolderItems.item(I).GetFolder.Items.Count - 1
				if objFolderItems.item(I).GetFolder.Items.item(J).Name = strTarget then
					objFolderItems.item(I).GetFolder.Items.item(J).InvokeVerb()
					Exit For
				end if
			Next
		end if
	Next

End Function
</SCRIPT>

</head>
<body>

<input type=button value="コンピュータ" onClick='Call OpenDesktopFile("::{20D04FE0-3AEA-1069-A2D8-08002B30309D}")'>
<input type=button value="コンピュータのプロパティ" onClick='Call OpenProp("::{20D04FE0-3AEA-1069-A2D8-08002B30309D}")'>
<br>

<input type=button value="ネットワーク" onClick='Call OpenDesktopFile("::{F02C1A0D-BE21-4350-88B0-7367FC96EF3C}")'>
<input type=button value="ネットワークのプロパティ" onClick='Call OpenProp("::{F02C1A0D-BE21-4350-88B0-7367FC96EF3C}")'>
<br>

<input type=button value="ごみ箱" onClick='Call OpenDesktopFile("::{645FF040-5081-101B-9F08-00AA002F954E}")'>
<input type=button value="ごみ箱のプロパティ" onClick='Call OpenProp("::{645FF040-5081-101B-9F08-00AA002F954E}")'>
<br>

<input type=button value="コントロールパネル" onClick='Call OpenDesktopFile("::{26EE0668-A00A-44D7-9371-BEB064C98683}")'>
<input type=button value="日付と時刻" onClick='Call ControlItemb("時計、言語、および地域", "日付と時刻")'>
<input type=button value="個人設定" onClick='Call ControlItemb("デスクトップのカスタマイズ", "個人設定")'>

</BODY>
</html>

```
