import * as React from 'react'

function PhoneBookForm({onSubmitPhoneBookEntry}) {
  const handleSubmit = e => {
    e.preventDefault()
    const firstName = e.target.elements.firstNameInput.value
    const lastName = e.target.elements.lastNameInput.value
    const phoneNumber = e.target.elements.phoneNumberInput.value
    onSubmitPhoneBookEntry({firstName, lastName, phoneNumber})
    document.getElementById('form').reset()
  }

  return (
    <form id="form" onSubmit={handleSubmit}>
      <div>
        <label htmlFor="input">First Name:</label>
        <input type="text" id="firstNameInput" />
      </div>
      <div>
        <label htmlFor="input">Last Name:</label>
        <input type="text" id="lastNameInput" />
      </div>
      <div>
        <label htmlFor="input">Phone number:</label>
        <input type="text" id="phoneNumberInput" />
      </div>
      <button type="submit">Submit</button>
    </form>
  )
}

function PhoneBook({firstName, lastName, phoneNumber}) {
  return (
    <tr>
      <td>{firstName}</td>
      <td>{lastName}</td>
      <td>{phoneNumber}</td>
    </tr>
  )
}

// sortBy function found on MDN at https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort
function sortBy(a, b) {
  const nameA = a.lastName.toUpperCase() // ignore upper and lowercase
  const nameB = b.lastName.toUpperCase() // ignore upper and lowercase
  if (nameA < nameB) {
    return -1
  }
  if (nameA > nameB) {
    return 1
  }

  // names must be equal
  return 0
}

function App() {
  const [phoneBookEntries, setPhoneBookEntries] = React.useState([])
  const onSubmitPhoneBookEntry = entry =>
    setPhoneBookEntries(
      [...phoneBookEntries, entry].sort((a, b) => sortBy(a, b)),
    )
  return (
    <div>
      <PhoneBookForm onSubmitPhoneBookEntry={onSubmitPhoneBookEntry} />
      <table>
        <tbody>
          {phoneBookEntries.map(({firstName, lastName, phoneNumber}) => (
            <React.Fragment key={phoneNumber}>
              <PhoneBook
                key={lastName}
                firstName={firstName}
                lastName={lastName}
                phoneNumber={phoneNumber}
              />
            </React.Fragment>
          ))}
        </tbody>
      </table>
    </div>
  )
}

export default App
