# DFA Simulator

# DFA Description
states = {'q0', 'q1', 'q2'}
alphabet = {'a', 'b'}

# Transition Table
transitions = {
    ('q0', 'a'): 'q1',
    ('q0', 'b'): 'q0',
    ('q1', 'a'): 'q1',
    ('q1', 'b'): 'q2',
    ('q2', 'a'): 'q1',
    ('q2', 'b'): 'q0'
}

# Initial State
initial_state = 'q0'

# Final State
final_states = {'q2'}

# Function to simulate DFA
def simulate_dfa(input_string):
    current_state = initial_state

    print("\nProcessing String:", input_string)
    print("State Transitions:")

    for symbol in input_string:
        if symbol not in alphabet:
            print("Invalid Symbol:", symbol)
            return

        print(current_state, "--", symbol, "-->", end=" ")

        current_state = transitions[(current_state, symbol)]
        print(current_state)

    if current_state in final_states:
        print("Result: Accepted")
    else:
        print("Result: Rejected")

# Accept multiple strings
n = int(input("Enter number of input strings: "))

for i in range(n):
    s = input(f"\nEnter String {i+1}: ")
    simulate_dfa(s)
