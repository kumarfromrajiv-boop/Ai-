message: text().notNull(),
  plan: text(),
  result: text(),
  cancelRequestedAt: timestamp('cancel_requested_at', { withTimezone: true }),
  dispatchHash: text('dispatch_hash'),
  createdAt: timestamp('created_at', { withTimezone: true }).defaultNow().notNull(),
  updatedAt: timestamp('updated_at', { withTimezone: true }).defaultNow().notNull(),
}, table => [uniqueIndex('one_active_job').on(sql`(1)`).where(sql`${table.status} IN ('queued', 'running')`)]);

export const jobMessages = pgTable('job_messages', {
  id: uuid().primaryKey(),
  jobId: uuid('job_id').notNull().references(() => jobs.id),
  role: text().notNull(),
  content: text().notNull(),
  createdAt: timestamp('created_at', { withTimezone: true }).defaultNow().notNull(),
});
