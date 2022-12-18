
\mathbf -- bold face
\mathbit --italic

```

Sub genEQ()
    Dim objRange As Range
    Dim objEq As OMath
    Dim AC As OMathAutoCorrectEntry
    Application.OMathAutoCorrect.UseOutsideOMath = True
    Set objRange = Selection.Range
    objRange.Text = "Celsius = \sqrt( \mathbf{X} +\mathbit{Y}) + sin(5/9 \times(Fahrenheit – 23 (\delta)^2))"
    For Each AC In Application.OMathAutoCorrect.Entries
        With objRange
            If InStr(.Text, AC.Name) > 0 Then
                .Text = Replace(.Text, AC.Name, AC.Value)
            End If
        End With
    Next AC
    Set objRange = Selection.OMaths.Add(objRange)
    Set objEq = objRange.OMaths(1)
    objEq.BuildUp
End Sub

```

```
    Dim AC As OMathAutoCorrectEntry
    
    Application.OMathAutoCorrect.UseOutsideOMath = True
    Set objRange = Selection.Range
    objRange.Text = "Y= \mathbf{X}\beta + \mathbf{Z}\mu + \mathbf{e}"
    objRange.Font.Size = 30

'    For Each AC In Application.OMathAutoCorrect.Entries
'        With objRange
'            If InStr(.Text, AC.Name) > 0 Then
'                .Text = Replace(.Text, AC.Name, AC.Value)
'            End If
'        End With
'    Next AC
    Set objRange = Selection.OMaths.Add(objRange)
    Set objEq = objRange.OMaths(1)

    objEq.BuildUp
    'objEq.Range.Font.Italic = False

    objRange.Select
    Selection.EndKey Unit:=wdLine
    Selection.Collapse wdCollapseEnd
    Selection.TypeText vbCr
    Selection.TypeText "where Y is the phenotype, b is regressor" & vbCr
    'ThisDocument.Content.Font.Name = "Times New Roman"
End Sub
```
