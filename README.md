Below is the solution:

Public Class frmMain
    'form load event
    Private Sub frmMain_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        lstNumber.Items.Clear() 'clears the list
        CenterToScreen() 'center on screen
    End Sub

    'Calculate button event
    Private Sub btnCalculate_Click(sender As Object, e As EventArgs) Handles btnCalculate.Click
        If rbtnFibonacii.Checked Then 'if fibonacii radio button is selected
            'declare variable
            Dim a As Int64 = 1
            Dim b As Int64 = 1
            Dim c As Int64
            Dim count As Integer = 3
            lstNumber.Items.Clear() 'clear the list item before adding to the list
            lstNumber.Items.Add("Fibonacci Numbers")
            'print the two number
            lstNumber.Items.Add("Term 1:" & vbTab & vbTab & a)
            lstNumber.Items.Add("Term 2:" & vbTab & vbTab & b)
            'loop 58 times
            Dim i As Integer = 1
            While i <> 60 - 2
                c = a + b
                a = b
                b = c
                lstNumber.Items.Add("Item " & count & ":" & vbTab & vbTab & c) 'add the fibonacii to the list
                count = count + 1
                i = i + 1
            End While
        ElseIf rbtnGeomatric.Checked Then ' if Harmonic Series radio button is selected
            'delcare the varibale
            lstNumber.Items.Clear() 'clear the list item before adding to the list
            Dim sum As Double = 1
            Dim count As Integer = 1
            Dim i As Integer = 1
            While i <> 1000 'loop 1000 times
                If i Mod 2 = 0 Then
                    sum = sum + 1.0 / i
                Else
                    sum = sum - 1.0 / i
                End If
                lstNumber.Items.Add("Sum to " & count & " term is:" & vbTab & sum.ToString("N5")) 'add the number to the list
                count = count + 1 'count the term
                i = i + 1
            End While
        ElseIf rbtnHarmonic.Checked Then 'if Geometric Series radio button is selected
            'declare the variable
            lstNumber.Items.Clear() 'clear the list item before adding to the list
            Dim i As Int64 = 1
            Dim s As Double = 0.0
            Dim b As Double = 1
            Dim count As Integer = 1
            'loop 25 times
            While i <> 25 'loop 1000 times
                s = s + 1 / i
                lstNumber.Items.Add("Sum to " & count & " term is:" & vbTab & vbTab & s.ToString("N5")) 'add the number to the list
                count = count + 1 'count the term
                i = i + 1
            End While
        ElseIf rbtnHailstoneSequence.Checked Then 'if Hailstone Sequence radio button is selected
            'declare the variabel
            Dim N As Integer = 56
            Dim x As Integer
            lstNumber.Items.Clear() 'clear the list
            lstNumber.Items.Add("Hamilton Sequence for " & N)
            'Function to generate Hailstone Numbers
            x = HailstoneNumbers(N)

            lstNumber.Items.Add(N & " tooks" & x & " terms")
        Else
            MessageBox.Show("Error! Please select the one option") 'error
        End If
    End Sub

    'method to generate the hailstone number
    Dim c As Integer
    Private Function HailstoneNumbers(n As Integer) As Integer
        lstNumber.Items.Add(n & vbNewLine) 'add the n value to the listbox
        If n = 1 And c = 0 Then 'if n = 1 and c = 0 the return
            Return c
        ElseIf n = 1 And Not c = 0 Then 'if n =0 and c = 0 the return
            c = c + 1 'increment the c by one
            Return c
        ElseIf n Mod 2 = 0 Then ' If n Is Even
            c = c + 1 'increment the c by one
            Return HailstoneNumbers(n / 2)
        ElseIf Not n Mod 2 = 0 Then 'if n Is Odd
            c = c + 1 'increment the c by one
            Return HailstoneNumbers(3 * n + 1)
        End If
        Return c 'return the count value
    End Function
End Class
