# Interaction Rules
- No <form> tags anywhere. All form elements in <div>s.
- All click handlers via addEventListener, not onclick=""
- Form validation: check all fields filled before any action
- On successful submission: replace entire form container 
  with confirmation message — do not just hide the form
- Smooth scroll: scrollIntoView({behavior:'smooth'})
- Never use alert() or confirm()
