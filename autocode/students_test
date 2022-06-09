package coverage

import (
	"os"
	"testing"
	"time"
)

// DO NOT EDIT THIS FUNCTION
func init() {
	content, err := os.ReadFile("students_test.go")
	if err != nil {
		panic(err)
	}
	err = os.WriteFile("autocode/students_test", content, 0644)
	if err != nil {
		panic(err)
	}
}

func TestPeopleLen(t *testing.T) {
	p_0 := People{}
	p_1 := People{}
	p_1 = append(p_1, Person{})
	p_2 := People{}
	p_2 = append(p_2, Person{})
	p_2 = append(p_2, Person{})

	len_0 := p_0.Len()
	if len_0 != 0 {
		t.Errorf("Expected: %d, got: %d", 0, len_0)
	}

	len_1 := p_1.Len()
	if len_1 != 1 {
		t.Errorf("Expected: %d, got: %d", 1, len_1)
	}

	len_2 := p_2.Len()
	if len_2 != 2 {
		t.Errorf("Expected: %d, got: %d", 2, len_2)
	}
}

func TestPeopleLess(t *testing.T) {
	p := People{}
	p = append(p, Person{
		firstName: "AAAA",
		lastName:  "AAAA",
		birthDay:  time.Date(2022, 1, 1, 0, 0, 0, 0, time.UTC),
	})
	p = append(p, Person{
		firstName: "AAAA",
		lastName:  "BBBB",
		birthDay:  time.Date(2022, 1, 1, 0, 0, 0, 0, time.UTC),
	})
	p = append(p, Person{
		firstName: "BBBB",
		lastName:  "AAAA",
		birthDay:  time.Date(2022, 1, 1, 0, 0, 0, 0, time.UTC),
	})

	p = append(p, Person{
		firstName: "CCCC",
		lastName:  "CCCC",
		birthDay:  time.Date(2025, 1, 1, 0, 0, 0, 0, time.UTC),
	})

	is_less_true := p.Less(0, 1)
	if !is_less_true {
		t.Errorf("Expected: %t, got: %t", true, is_less_true)
	}

	is_less_true = p.Less(0, 2)
	if !is_less_true {
		t.Errorf("Expected: %t, got: %t", true, is_less_true)
	}

	is_less_false := p.Less(0, 3)
	if is_less_false {
		t.Errorf("Expected: %t, got: %t", false, is_less_false)
	}
}

func TestPeopleSwap(t *testing.T) {
	p := People{}
	p = append(p, Person{
		firstName: "AAAA",
		lastName:  "AAAA",
		birthDay:  time.Date(2022, 1, 1, 0, 0, 0, 0, time.UTC),
	})
	p = append(p, Person{
		firstName: "CCCC",
		lastName:  "CCCC",
		birthDay:  time.Date(2025, 1, 1, 0, 0, 0, 0, time.UTC),
	})

	p.Swap(0, 1)

	if p[0].firstName != "CCCC" {
		t.Errorf("Expected: %s, got: %s", "CCCC", p[0].firstName)
	}
	if p[1].firstName != "AAAA" {
		t.Errorf("Expected: %s, got: %s", "CCCC", p[1].firstName)
	}
}

func TestNewMatrix(t *testing.T) {
	input := `1 2 3
4 5 6`
	m, err := New(input)
	if m == nil {
		t.Errorf("Nil matrix for valid matrix string")
	}
	if err != nil {
		t.Errorf("Error for valid matrix string")
	}
	input = `1 2
3 4 5 6`
	m, err = New(input)
	if m != nil {
		t.Errorf("Return matrix for invalid matrix string")
	}
	if err == nil || err.Error() != "Rows need to be the same length" {
		t.Errorf("Error is nil or invalid error message")
	}
	input = `a 2 3
4 5 6`
	m, err = New(input)
	if m != nil {
		t.Errorf("Return matrix for invalid matrix string")
	}
	if err == nil {
		t.Errorf("Error don't detected for invalid input data")
	}
}

func TestRowsMatrix(t *testing.T) {
	input := `1 2 3
4 5 6`
	m, _ := New(input)
	rr := m.Rows()

	expected := [][]int{{1, 2, 3}, {4, 5, 6}}

	if len(rr[0]) != len(expected[0]) ||
		rr[0][0] != expected[0][0] ||
		rr[0][1] != expected[0][1] ||
		rr[0][2] != expected[0][2] {
		t.Errorf("Row 0 is not equal")
	}

	if len(rr[1]) != len(expected[1]) ||
		rr[1][0] != expected[1][0] ||
		rr[1][1] != expected[1][1] ||
		rr[1][2] != expected[1][2] {
		t.Errorf("Row 1 is not equal")
	}
}

func TestColsMatrix(t *testing.T) {
	input := `1 2 3
4 5 6`
	m, _ := New(input)
	cols := m.Cols()

	expected := [][]int{{1, 4}, {2, 5}, {3, 6}}

	if len(cols[0]) != len(expected[0]) ||
		cols[0][0] != expected[0][0] ||
		cols[0][1] != expected[0][1] {
		t.Errorf("Col 0 is not equal")
	}

	if len(cols[1]) != len(expected[1]) ||
		cols[1][0] != expected[1][0] ||
		cols[1][1] != expected[1][1] {
		t.Errorf("Col 1 is not equal")
	}

	if len(cols[2]) != len(expected[2]) ||
		cols[2][0] != expected[2][0] ||
		cols[2][1] != expected[2][1] {
		t.Errorf("Col 2 is not equal")
	}
}

func TestSetMatrix(t *testing.T) {
	input := `1 2 3
4 5 6`
	m, _ := New(input)
	result := m.Set(-1, 0, 999)

	if result != false {
		t.Errorf("Dont detected invalid param")
	}

	result = m.Set(0, 0, 999)

	if result != true {
		t.Errorf("Cannot set new value to matrix")
	}
}
