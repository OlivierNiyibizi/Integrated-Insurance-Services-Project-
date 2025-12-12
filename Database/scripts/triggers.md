**here is to create trigger**

CREATE OR REPLACE TRIGGER trg_validate_payment
BEFORE INSERT ON CUSTOMER_POLICY
FOR EACH ROW
DECLARE
    v_payment NUMBER;
BEGIN
    SELECT COUNT(*) INTO v_payment
    FROM PAYMENT
    WHERE Customer_policy_id = :NEW.Customer_policy_id
      AND Amount_paid >= (SELECT Premium_amount FROM POLICY WHERE Policy_id = :NEW.Policy_id);

    IF v_payment = 0 THEN
        RAISE_APPLICATION_ERROR(-20001, 'Payment required before activating policy.');
    END IF;
END;
/
